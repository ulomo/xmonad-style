# 202105

之前用过xmobar，但是觉得配置的不怎么好看就转而使用polybar，后来在youtube上面看到DT的xmobar配置非常nice，所以还是用xmobar吧，毕竟这个搭配xmonad才是最棒的。其中关于xmobar的配置基本上就是抄的DT的配置，只修改了一部分，其中获取音量和获取系统更新提醒的脚本使用go语言重新写了一下（xmobar的配置及两个go脚本都放在`~/.config/xmobar`下），比shell调用消耗系统资源小，毕竟它的调用频率比较高。

xmonad的配置放在`~/.xmonad`下，需要编译`xmonad --recompile`后才可用

其它脚本可放在`~/.local/bin`目录下，同时在`/etc/profile`中添加`append_path "$HOME/.local/bin"`声明脚本路径


## 功能介绍

注意xmonad的操作中的modkey默认为win键，我将win和caps进行了调换方便操作，调换的脚本为`.Xmodmap`，放在home目录下.

 > window layout

  1. 关于窗口样式：采用了三种，一种是平铺，一种是堆叠（默认），还有一种系统自带的悬浮（modkey+alt+鼠标左键/右键），使用快捷键modkey+space切换。
     [![gJNB5D.png](https://z3.ax1x.com/2021/05/09/gJNB5D.png)](https://imgtu.com/i/gJNB5D)
     [![gJNs8H.png](https://z3.ax1x.com/2021/05/09/gJNs8H.png)](https://imgtu.com/i/gJNs8H)
     [![gJNrPe.png](https://z3.ax1x.com/2021/05/09/gJNrPe.png)](https://imgtu.com/i/gJNrPe)  

  2. 平铺的窗口样式做了动态调整，但是基础只有两种（tile，gird），没整其它花里胡哨的。当只有一个窗口时居中，两个/三个时正常的tile，四个及以上grid。
  3. 窗口的border边框也支持动态调整，一个窗口时无边框，多于一个时才会有边框。

 > 最重要的一个快捷键
 
 1. 打开终端：`modkey+n`
 
 > 窗口操作

  1. 最大化： `modkey+f`
  2. 菜单：`modkey+m`
  3. 删除一个窗口：`modkey+backspace`
  4. 删除工作组的窗口：`modkey+\+backspace`
  5. 复制窗口到所有工作组：`modkey+\+y`
  6. 删除其它所有复制的窗口：`modkey+\+d`
  7. 隐藏窗口：`modkey+0`
  8. 取消隐藏：`modkey+\+0`
  9. 切换当前窗口边框：`modkey+shift+b`
  10. 切换工作组窗口边框：`modkey+w+b`
  11. 增加窗口间距：`modkey++`或者`modkey+alt++`
  12. 减小窗口间距：`modkey+-`或者`modkey+alt+-`
  13. 窗口间移动：`modkey+h/j/k/l`
 
 > 窗口合并
 
  1. 向左合并：`modkey+w+h`
  2. 向右合并：`modkey+w+l`
  3. 向上合并：`modkey+w+k`
  4. 向下合并：`modkey+w+j`
  5. 合并所有：`modkey+w+m`
  6. 取消所有合并：`modkey+w+u`
  7. 在合并的窗口中移动：`modkey+]`或者`modkey+[`

 > 工作组操作

  1. 右移：`modkey+o`
  2. 左移：`modkey+i`
  3. 指定移动到某个工作组：`modkey+\+数字` 或者`modkey+数字`
  4. 在最近两个工作组间切换：`alt+tab`
 
 > scratchpad

  1. terminal1:`modkey+u`
  2. terminal2:`modkey+shift+i`
  3. terminal3:`modkey+shift+o`
  4. 文件管理器：`modkey+e` （需要安装nautilus）
  5. 便签：`modkey+s` （需要安装xpad）

 > 鼠标手势

  1. 下个工作组：`modkey+点击鼠标右键左滑`
  2. 上个工作组：`modkey+点击鼠标右键右滑`
  3. 窗口最大化：`modkey+鼠标右键上滑`
  4. 顶部终端：`modkey+鼠标右键下滑`
  
 > 其它快捷键
 
  1. 软件截屏：`modkey+\+p` （需要安装flameshot）
  2. 全屏截屏：`modkey+p`  （需要安装ffcast）
  3. 音量加：`modkey+f3`  （需要安装pamixer）
  4. 音量减：`modkey+f2`
  5. dmenu:`modkey+r` （需要安装dmenu）
  6. 启动动态壁纸切换：`modkey+\+w` (需要脚本wallpaper+安装feh)
  7. 锁屏：`modkey+\+l`  （需要安装slock）
  8. 启动firefox：`modkey+\+f` （需要安装firefox）
  9. 启动win10虚拟机：`modkey+\+e` (需要存在win10虚拟机且命名为windows10)
  10. 隐藏taskbar:`modkey+\+b`
  11. 打开screenkey:`modkey+\+k` (需要脚本showkey+安装screenkey)
  12. 翻译选中的词或句子：`modkey+t` (需要脚本translate+安装ydcv-rs-git mplayer)

 > 悬浮窗口
 
  1. 悬浮移动：`modkey+alt+鼠标左键`
  2. 悬浮大小：`modkey+alt+鼠标右键`
  3. 取消悬浮：`modkey+w+t`


 > 最后说一下个人觉得特别nice的几个操作
 
  1. `mod+f`随时切换全屏窗口
  2. `alt+tab`和window一样的键位，快速在最近两个工作组间移动
  3. `mod+t`随时翻译选中的单词或句子，很丝滑
  4. `mod+m`将窗口在工作组间的移动
  5. `mod+p`或者`mod+\+p`截屏
  6. `mod+\+y`复制窗口到所有工作组，一边写东西一边看剧不要太爽
  7. `mod+s`非常便捷的便签
  8. `mod+u`随时可调用的终端
