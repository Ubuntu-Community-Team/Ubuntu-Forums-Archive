---
title: "Can I delete svn trunk after make install?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by jonastpetersen on 2009-08-25
Hi Everybody

I'm complete new to linux (ubuntu) and still trying to figure out how most of this works. I needed the program ffmpeg (because I want to play around with openCV) and was able to install it by following a guide. It basically told me to do the following:

1. Check it out using "svn co [http://ffmpeg.mplayer](http://ffmpeg.mplayer)....
2. ./configure --enable-shared
3. make
4. sudo make install

As a former windows guy I'm not completely sure what is going on here, especially the "make install" part. But I can see that I have gotten the files I was supposed to in my usr/local folder, so it seems to have worked. Now my question is, can I just delete the files I checked out from svn, or are they still needed?

Thanks in advance
Jonas

---

### Post by Tibuda on 2009-08-25
Yes, you can, but you won't be able to uninstall it later with "sudo make uninstall". When installing from source code, I suggest you to use "sudo [checkinstall]("apt:checkinstall")" instead of "sudo make install", so the application can be uninstalled from Synaptic. It will also create a .deb package installer for you.

---

### Post by MrWES on 2009-08-25
> **danielrmt said:**
> Yes, you can, but you won't be able to uninstall it later with "sudo make uninstall". When installing from source code, I suggest you to use "sudo [checkinstall]("apt:checkinstall")" instead of "sudo make install", so the application can be uninstalled from Synaptic. It will also create a .deb package installer for you.

You won't be able to issue the 
```
svn up
```
command to update either.

+1 for checkinstall
[https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

Bill

---

### Post by FakeOutdoorsman on 2009-08-25
You can see a checkinstall example with FFmpeg here:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by jonastpetersen on 2009-08-25
Thanks for the answers everybody. I appreciate it!

---

### Post by Keith Hedger on 2009-08-25
if you just want to save space you can use```
make clean
```or```
make dist clean
``` this still allows you to do an svn update or uninstall in the futre

---

