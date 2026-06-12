---
title: "Problem installing Flash Player (64-bit)"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by letters on 2008-12-22
Hello everyone. This is my first time using Ubuntu. I am having problems installing Adobe Flash Player. Ive downloaded install_flash_player_10_linux.deb, but before I can click Install Package in the Package Installer it says... Status: Error: Wrong architecture 'i386'. I was wondering if anyone could help me with this problem. Thank you.:)

---

### Post by taurus on 2008-12-22
Are you running the x86_64 version?

Applications -> Accessories -> Terminal
```
uname -a
```

---

### Post by letters on 2008-12-22
Hello. Yes.

Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux

I dont know what to do. I still get the error. :(

---

### Post by igknighted on 2008-12-22
You need the 64bit version of flash player.  It is still a beta, so you need to get it from the adobe labs page.

EDIT: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by letters on 2008-12-22
Thank you igknighted. Ive downloaded the 64 bit version flash player. Ive extracted the file. How do I install flash player? Thank you.

---

### Post by igknighted on 2008-12-22
> **letters said:**
> Thank you igknighted. Ive downloaded the 64 bit version flash player. Ive extracted the file. How do I install flash player? Thank you.

There should be a readme file there, all you need to do is move the file to the folder it indicates (Should be /usr/lib64/mozilla IIRC)

---

### Post by taurus on 2008-12-22
> **igknighted said:**
> There should be a readme file there, all you need to do is move the file to the folder it indicates (Should be /usr/lib64/mozilla IIRC)

There's no readme for this one.  

You probably saved it, libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz, to your desktop so open a terminal and run

```
cd ~/Desktop
tar xvzf libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
```
Now, you should have a new file called libflashplayer.so.  You need to move that to ~/.mozilla/plugins.  If you don't have that file, create it first.

```
mkdir ~/.mozilla/plugins
mv libflashplayer.so ~/.mozilla/plugins
```
Restart firefox and see if flashplugin works this time.

---

### Post by igknighted on 2008-12-22
Thanks taurus, I didn't realize the labs one didn't come with the readme.

---

### Post by letters on 2008-12-22
Thank you very much taurus and igknighted. Flash Player is installed and working fine. Ubuntu forums is great! :p

---

