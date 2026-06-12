---
title: "Installing Bespin..."
date: 2010-05-21
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-05-21
I'm having some problems compiling Bespin from the SVN on Linux Mint 8 'Helena' (Kubuntu 9.10 'karmic')
I followed the Ubuntu Evolution Tut --> [http://ubuntuevolution.wordpress.com/2010/01/07/nice-bespin-kde-4-desktop-part-1/](http://ubuntuevolution.wordpress.com/2010/01/07/nice-bespin-kde-4-desktop-part-1/)

until I got to the second part of "Download & Installing of Bespin Style" I'd gone into the build folder and typed 'make' however after getting to 96% I get errors:confused:

```
#
[ 96%] Building CXX object kwin/CMakeFiles/kwin_bespin_config.dir/config.o                                                                    
#
In file included from /home/carl/src/cloudcity/kwin/config.cpp:27:                                                                            
#
/home/carl/src/cloudcity/kwin/../config/bconfig.h:98: warning: ‘virtual bool BConfig::save()’ was hidden                                      
#
/home/carl/src/cloudcity/kwin/config.h:45: warning:   by ‘void Config::save(KConfigGroup&)’                                                    
#
/home/carl/src/cloudcity/kwin/config.cpp: In member function ‘void Config::catchClones(QListWidgetItem*)’:                                    
#
/home/carl/src/cloudcity/kwin/config.cpp:245: warning: suggest parentheses around assignment used as truth value
#
Linking CXX shared module ../lib/kwin_bespin_config.so
#
[ 96%] Built target kwin_bespin_config
#
Scanning dependencies of target plasma_applet_xbar_automoc
#
Generating dbus.moc
#
Generating xbar.moc
#
Generating moc_menubar.cpp
#
[ 96%] Built target plasma_applet_xbar_automoc
#
Scanning dependencies of target plasma_applet_xbar
#
[ 97%] Building CXX object XBar/CMakeFiles/plasma_applet_xbar.dir/plasma_applet_xbar_automoc.o
#
[ 98%] Building CXX object XBar/CMakeFiles/plasma_applet_xbar.dir/menubar.o
#
/home/carl/src/cloudcity/XBar/menubar.cpp:99: warning: unused parameter ‘constraint’
#
[100%] Building CXX object XBar/CMakeFiles/plasma_applet_xbar.dir/xbar.o
#
/home/carl/src/cloudcity/XBar/xbar.cpp: In member function ‘virtual void XBar::init()’:
#
/home/carl/src/cloudcity/XBar/xbar.cpp:146: error: ‘class QVariant’ has no member named ‘toFloat’
#
/home/carl/src/cloudcity/XBar/xbar.cpp: At global scope:
#
/home/carl/src/cloudcity/XBar/xbar.cpp:550: warning: unused parameter ‘type’
#
make[2]: *** [XBar/CMakeFiles/plasma_applet_xbar.dir/xbar.o] Error 1
#
make[1]: *** [XBar/CMakeFiles/plasma_applet_xbar.dir/all] Error 2
#
make: *** [all] Error 2

```
Full output of 'make' --> [http://pastebin.com/BxR6fzSh](http://pastebin.com/BxR6fzSh)

Thanks in advance!:guitar:

---

