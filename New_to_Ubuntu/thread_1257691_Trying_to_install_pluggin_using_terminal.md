---
title: "Trying to install pluggin using terminal"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by vlad1975 on 2009-09-04
Hello,

I am having difficulty installing this plugging.

please advise what i am doing wrong.


ed@ed-desktop:~/Desktop/pidgin-fonomobutton-0.1.5$ sudo make all install
[sudo] password for ed: 
gcc `pkg-config pidgin --cflags --libs` --shared -Wall -O2 fonomobutton.c -o fonomobutton.so
Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
fonomobutton.c:25:18: error: glib.h: No such file or directory
fonomobutton.c:36:20: error: notify.h: No such file or directory
fonomobutton.c:37:20: error: plugin.h: No such file or directory
fonomobutton.c:38:21: error: version.h: No such file or directory
fonomobutton.c:40:20: error: pidgin.h: No such file or directory
fonomobutton.c:42:21: error: gtkconv.h: No such file or directory
fonomobutton.c:43:23: error: gtkplugin.h: No such file or directory
fonomobutton.c:45:26: error: conversation.h: No such file or directory
fonomobutton.c:46:24: error: gtkconvwin.h: No such file or directory
fonomobutton.c:48:23: error: gtkimhtml.h: No such file or directory
fonomobutton.c:55: error: expected ‘)’ before ‘*’ token
fonomobutton.c:87: error: expected ‘)’ before ‘*’ token
fonomobutton.c:132: error: expected ‘)’ before ‘*’ token
fonomobutton.c:152: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_load’
fonomobutton.c:175: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_unload’
fonomobutton.c:193: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘info’
fonomobutton.c:227: error: expected ‘)’ before ‘*’ token
fonomobutton.c:231: warning: return type defaults to ‘int’
fonomobutton.c: In function ‘PURPLE_INIT_PLUGIN’:
fonomobutton.c:231: error: expected ‘{’ at end of input
make: *** [all] Error 1
ed@ed-desktop:~/Desktop/pidgin-fonomobutton-0.1.5$

---

### Post by Bölvaður on 2009-09-04
google told me this


[http://ubuntuforums.org/archive/index.php/t-1162876.html]("http://ubuntuforums.org/archive/index.php/t-1162876.html")

even though the error message isnt identical the same core problem is. look at the last post

---

### Post by jimingkui on 2009-09-04
First install pidgin-dev
sudo apt-get install pidgin-dev

---

