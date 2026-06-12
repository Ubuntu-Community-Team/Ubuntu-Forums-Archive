---
title: "64-bit Real Player help needed"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Digital Hick on 2009-05-16
Downloaded 64-bit real player .tar.bz2 file, opened up, and all I have is a bunch of stuff that will not execute.  Nothing wants to install, nothing want to run, nothing wants to respond to ./configure.  Anyone have any ideas?

//Edit
Go to my last post here...

---

### Post by oldos2er on 2009-05-16
What's in the tar.bz2? Can you post a file list?

---

### Post by Sealbhach on 2009-05-16
Can you not use the .deb file supplied on the Real Player download page? 

[http://www.real.com/linux](http://www.real.com/linux)

Does it have to be 64bit?


.

---

### Post by Digital Hick on 2009-05-17
The 32-bit deb is rejected as wrong architecture, attempting to do a dpkg intall with force architecture does not work, in fact causes chaos.

---

### Post by mc4man on 2009-05-17
I think you should read thru here even though it hasn't been updated in a while (for 64 bit  info  scroll down a bit

I happen to be on a 9.04 64 bit live cd, maybe I'll give it a try
[https://help.ubuntu.com/community/RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealPlayerInstallationMethods)

Edit : that page is a bit outdated, wasn't that hard to install, the player works ok with .rmvb sample
As far as using as firefox plugin if that's your intention I'd search out or browse thru here

[http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

had to install libstdc++5 first
to install just did this ( at directory prompt for extracted folder
ubuntu@ubuntu:~/realplay-11.1.1.1747-linux-2.6-glibc23-amd64$ sudo ./realplay.bin

---

### Post by Digital Hick on 2009-05-22
Consider this thread solved.
The solution was to move to 32-bit Ubuntu.
The file I got from Real Player for the 64-bit version was a MANUAL install.
No thanks!
Give me a .deb or don't bother.:)

---

### Post by six616 on 2009-08-13
#source from [http://forum.ubuntu.org.cn/viewtopic.php?f=85&t=147898](http://forum.ubuntu.org.cn/viewtopic.php?f=85&t=147898)
sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 Linux-headers-$(uname -r)
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms
sudo apt-get install ia32-libs
sudo apt-get install util-Linux

#install lib32asound2 by Synaptic
System >Adminstration> Synaptic, search "lib32asound2", and install it.

#Download and install RealPlayer11 from [http://www.real.com/linux](http://www.real.com/linux)
sudo chmod 755 ./RealPlayer11GOLD.bin
sudo ./RealPlayer11GOLD.bin

---

### Post by halitech on 2009-08-13
why not use xine? it will play rm files

---

