---
title: "Installing yawp problems"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Hollyecho_Montgomery on 2011-03-03
I need to know what I am missing.  I am trying to install yaWP.

This is what I got as a message:

hollyecho@Presario-F500-GF596UA-ABA:~$ sudo aptitude install build-essential
[sudo] password for hollyecho: 
sudo: aptitude: command not found
hollyecho@Presario-F500-GF596UA-ABA:~$ cd Downloads
hollyecho@Presario-F500-GF596UA-ABA:~/Downloads$ bunzip2 yawp-0.3.6.tar.bz2
hollyecho@Presario-F500-GF596UA-ABA:~/Downloads$ tar xf yawp-0.3.6.tar
hollyecho@Presario-F500-GF596UA-ABA:~/Downloads$ cd yawp-0.3.6
hollyecho@Presario-F500-GF596UA-ABA:~/Downloads/yawp-0.3.6$ ./configure
bash: ./configure: No such file or directory
hollyecho@Presario-F500-GF596UA-ABA:~/Downloads/yawp-0.3.6$ ./install.sh
DEBUG: -DCMAKE_BUILD_TYPE=Release
UNITTESTS: 
LOGLEVEL: -DDEBUG_LOGLEVEL=Debug
LOGFILE: -DDEBUG_LOGFILE=/tmp/yawp.log
./install.sh: line 209: cmake: command not found
**[COLOR=Red]CMake failed. Your system probably does not meets all requirements.[/COLOR]**
hollyecho@Presario-F500-GF596UA-ABA:~/Downloads/yawp-0.3.6$ 

How can I solve this?  Its a weather program, I replaced my Win7Ulti for  Kubuntu 10.10, I had 1st installed Ubuntu 10.10, and thought this might  (Kubuntu) might be an easier trans, but, I have lots of problems  installing anything else but straight .deb files.  

Help please??

My hardware report:  For I know someone will ask, I have reading this forums, I just can't find an answer that works for me.
[IMG]http://hollyecho.com/images/system-info1.png[/IMG]

[IMG]http://hollyecho.com/images/system-info2.png[/IMG]



Fear is like a virus, it spreads quickest among the weak.  Hollyecho Montgomery

---

### Post by kellemes on 2011-03-03
try sudo apt-get install build-essential

---

### Post by james_xxx on 2011-03-03
Firstly, it appears that aptitude is not installed on your system.

You should read up on both the similarities and differences between apt-get and aptitude.

You can install aptitude using apt-get:
```
sudo apt-get update && sudo apt-get install aptitude
```

Secondly, it is unnecessary to compile YAWP yourself. There are compiled binaries available for KDE 4.5.1.

Just do the following:
```
sudo apt-get install plasma-widget-yawp
```

---

### Post by Hollyecho_Montgomery on 2011-03-09
Thank you ever so much, sorry it took so long to reply, but I had never gotten notification that there was a reply.   PERFECT, thank you - it is working great now, and it is a great little weather station.  ):P

---

