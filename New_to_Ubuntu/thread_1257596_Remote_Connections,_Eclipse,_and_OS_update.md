---
title: "Remote Connections, Eclipse, and OS update"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by jumpboy on 2009-09-04
Hi all, 3 quick questions from a Linux/Ubuntu noobie.

1) I installed Ubuntu desktop on my netbook out of a moment of hatred of XP. I want the netbook version now and wondering if I can update the desktop version without doing a clean install of the OS.

2) I need to do a remote connection to use MATLAB off my school's server. Typing in ssh -X blah blah blah gets annoying so is there a way I can get a script together to have on my desktop to skip these things or a program (I'm sure there is)?

3) I need Eclipse 3.5 for a programming course. I can't get it to work even though I've tried installing the JRE and JDK. The eclipse folder is on my desktop btw. And I got the version info below.


netbook:--$ java -version 
The program ‘java’ can be found in the foUowing packages: 
* gij4.3 
* java-gcj -compact-headless 
* openjdk-6-jre-headless 
* cacao 
* gij-4.2 
* jamvm 
* kaffe 
Try: sudo apt-get instaU <selected package> 
bash: java: command not found

---

### Post by nothingspecial on 2009-09-04
1. ```
sudo apt-get install go-home-applet human-netbook-theme maximus ume-launcher window-picker-applet && sudo /etc/init.d/gdm restart
```

2 Make an alias
```

nano .bashrc
```

At the end of the file put, well I have one that goes

```
alias server='ssh -X -C -c blowfish me@192.168.2.6'
```

Now I just have to type ```
server
``` alter it to your needs.

You have to restart bash for it to take effect.

```
bash
```

---

### Post by Nepherte on 2009-09-04
Install the ubuntu-restricted-extras package. Among other things, it contains sun-java6-jre.
```
sudo apt-get install sun-java6-jre
```
For JDK, you need to explicitly install sun-java6-jdk:
```
sudo apt-get install sun-java6-jdk
```

If you have downloaded eclipse yourself, just run the eclipse file in that directory. If it doesn't work, try running it from the terminal and see what error messages it gives you.

---

### Post by jumpboy on 2009-09-04
thanks for the replies.

The command line for the Netbook remix didn't work. said "E: Couldn't find package umd-launcher"

The JDK failed the first time I tried to install too with the same code. Trying again but looks like it stopped working even though my wireless connection is still fine. 

Haven't give the Alias thing a go yet.

---

