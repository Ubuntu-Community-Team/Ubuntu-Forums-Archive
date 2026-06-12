---
title: "Video Drivers Problem"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by stevoo on 2009-04-26
Can i please get some help in installing the correct drivers for my 9.04.

I cant really remember what i had on 8 since i did a fresh install.

The problem is that i use this laptop and split screen with a tv.  i just use this like a media center.
When ever i split the screen i get various error :
```

Major opcode of failed request: 1 (X_CreateWindow) Serial number of failed request: 21 Current serial number in output stream: 22 CRITSEC[0x8bed5e4]: Trying to enter destroyed section. CRITSEC[0x8bed5e4]: Trying to leave destroyed section
```

Also i get complains from xbmc with the same errors and the laptop screen is decreased by  2 - 3 points on each side while the tv one looks ok.

But no video will show when i am in split mode.

When i reconfigure the graphics and revert back to single display then the video is displayed normally. XBmc is still complaining that i need opengl there. 

my lspci : 
```
stevoo@stevooOnUbuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)

```



So anyone ? who know what i need to install in order to be ok with this ? 

cheers

---

