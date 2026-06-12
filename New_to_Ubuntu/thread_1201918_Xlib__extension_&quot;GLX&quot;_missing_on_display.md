---
title: "Xlib:  extension &quot;GLX&quot; missing on display &quot;:0.0&quot; nvidia driver"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Beware The Birchmen on 2009-07-01
Hello Friends
My graphics card is nvidia geforce 9100m g.

I just installed Ubuntu 9.04. First I tried to manually install the latest nvidia driver, NVIDIA-Linux-x86-185.18.14-pkg1.run. However, that failed and I had to get Ubuntu to fix it via repair mode in Grub.

Afterwards I downloaded Envy and ran that. It installed driver:180.44 according to NVIDIA X server Settings under system>admin tools. 

THE PROBLEM:
in NVIDIA X server settings if I click on Open GL/GLX server information it says: Fail to query the GLX server vendor.
If I run glxgears from terminal it says:
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

The 180.44 driver is installed because the graphics are much better than the fresh install, also the Nvidia logo pops up before login. However, I can't turn on graphic effects at all and it seems no 3d applications will work.

Please advise what I should do :( I've been messing with this all afternoon any help would be much appreciated.
Thank you for your time.

---

### Post by Beware The Birchmen on 2009-07-01
No opengl applications work :( please help

---

### Post by Beware The Birchmen on 2009-07-01
:guitar::guitar::guitar::guitar::guitar::guitar:


i followed the guide located here [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
tinivole ):P awesome stuff man. thank you!

problem seems solved. glxgears runs now and opengl games seem to be working8-)

---

