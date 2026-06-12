---
title: "VLC crashing when opening any file."
date: 2009-03-18
forum: New to Ubuntu
---

### Post by loklaan on 2009-03-18
Hi there! First post!x3

I've looked everywhere but I can't find any solutions. Need help, VLC is crashing everytime I open any file. 

It must have something to do with its gui because when I open with files with 'cvlc' (no gui just play) it works fine, well a bit wrong with the scanning frequency but :s.

```
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[????????] x11 video output error: X11 request 2.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Serial number of failed request:  467
  Current serial number in output stream:  468
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb49007c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb490096e]
#2 /usr/lib/libX11.so.6 [0xb2279619]
#3 /usr/lib/libXrender.so.1(XRenderFreePicture+0x41) [0xb490df41]
#4 /usr/lib/libQtGui.so.4 [0xb25336bf]
#5 /usr/lib/libQtGui.so.4 [0xb253417d]
#6 /usr/lib/libQtGui.so.4(_ZN7QPixmap5derefEv+0x5d) [0xb25289ad]
#7 /usr/lib/libQtGui.so.4(_ZN7QPixmapD2Ev+0x30) [0xb2528e10]
#8 /usr/lib/libQtGui.so.4 [0xb252e0ba]
#9 /usr/lib/libQtGui.so.4 [0xb252e72f]
#10 /usr/lib/libQtGui.so.4 [0xb252dd5a]
#11 /lib/tls/i686/cmov/libc.so.6(exit+0x89) [0xb7df1d89]
#12 /usr/lib/libX11.so.6 [0xb2271d4e]
#13 /usr/lib/vlc/video_output/libxvideo_plugin.so [0xb078ba60]
QWaitCondition: cv destroy failure: 
QWaitCondition: mutex destroy failure:
```

Thats where the errors occured, someone helplease!x4

---

### Post by iamkrazee on 2009-03-18
I have seen this, I just upgraded my vlc at that point, and it got fixed. Not quite sure what the problem was, or the solution for that matter. Just know how it got fixed.. on its own.

---

### Post by binbash on 2009-03-18
go to vlc properties and change the video output to X11

---

### Post by loklaan on 2009-03-18
> **binbash said:**
> go to vlc properties and change the video output to X11

Thanks, but unfortunately it didn't work. >.>
It's definitely something to do with the interface module:

```
-- logger module started --
main: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
main error: no suitable interface module
main error: interface "rc" initialization failed
logger: using logger...
```

Ran the logger in vlc and it spat out that...

I've tried apt-get removing it and re-installing to no effect.

---

### Post by illmatic on 2009-03-18
is your graphic driver running properly?
I had a problem maximising videos with vlc, because my graphic driver wasn't installed right.

---

### Post by loklaan on 2009-03-18
To the best of my knowledge yes, I'm using the propriety drivers for nvidia (v177).
I could fix the vlc crashes with a restart before, it no longer does that anymore though. :(

---

### Post by loklaan on 2009-03-18
bump in hope for reply

---

### Post by loklaan on 2009-03-18
I've tested with other skins, and you CAN imbed video into the skins interface through opening the video file whilst having vlc open. But if I open a file say with double click, the video plays through cvlc... Annoying >.<

---

### Post by loklaan on 2009-03-19
bump

---

### Post by Alex82 on 2009-03-19
Have a look at this post mate....

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

it got things sorted for me

---

### Post by khelben1979 on 2009-03-19
If you're missing the file repositories for VLC you'll find information about how to fix this [here]("http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html").

It will make sure you have the latest version of VLC at all times.

---

### Post by loklaan on 2009-03-20
I've used the Synaptic Package Manager to completely remove and reinstall vlc but it doesnt help, does it delete ALL vlc files?

---

### Post by khelben1979 on 2009-03-20
In your home catalog you have a couple of files which is used by VLC and you have it in the .vlc catalog.

You can try this:
```
sudo mv /home/[user]/.vlc/ /home/[user]/.vlc-old
```

---

### Post by loklaan on 2009-03-20
I didn't happen to find /home/[me]/.vlc but instead /home/[me]/.config/vlc, thanks that cool to know - the hidden local files that is.

Didn't help though >..<

I think I need to COMPLETELY purge all files made by the install and the installs themeselves, but I don't know where they are??

---

### Post by khelben1979 on 2009-03-20
Have you tried (?):
```
sudo apt-get purge vlc
```

---

### Post by loklaan on 2009-03-20
Yeah it gets rid of the hidden local config files actually, but not the local install files that I think we're after >.<

---

### Post by loklaan on 2009-03-23
Its the stupid default skin, im not sure why it can't imbed videos in its interface, but it just can't.

---

