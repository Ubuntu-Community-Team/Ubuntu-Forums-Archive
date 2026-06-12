---
title: "after installing mac4lin i can no longer use the desktop effects???"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by ecwasnthere on 2009-10-27
i was able to use the desktop effects but after installing mac4lin i no longer can, i tried to enable compiz in the terminal thinking that it just was enabled and if i run the good ol $ compiz --replace i get this
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1360x768) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

any ideas??? im using ubuntu jaunty, my graphics card is a nvidia geforce 9500 gt and can support the 3d effects.

---

### Post by martrn on 2009-10-27
> **ecwasnthere said:**
> any ideas??? im using ubuntu jaunty, my graphics card is a nvidia geforce 9500 gt and can support the 3d effects.

I do not belive you have your nvidia binary drivers installed properly, have installed the incorrect type of nvidia biniary drivers (there are two), or else you have a misconfiguration of your X11 configuration files/screen.  There is nothing in the mac4lin that would cause this problem that you describe.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")


If you have the nvidia binary drivers installed properly and defiantly know this then your need to modify your xorg.conf file and ensure you are loading the correct modules, nvidia is particular about the xorg.conf file being set up properly.
[https://help.ubuntu.com/community/Video]("https://help.ubuntu.com/community/Video")
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

---

### Post by ecwasnthere on 2009-10-27
i found a thread that explained it heres a link in case others need it 
[http://ubuntuforums.org/showthread.php?t=1232865](http://ubuntuforums.org/showthread.php?t=1232865)
thanks much all

---

