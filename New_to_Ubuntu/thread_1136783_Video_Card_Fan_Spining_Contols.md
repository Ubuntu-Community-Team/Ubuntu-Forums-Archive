---
title: "Video Card Fan Spining Contols???"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by aas452 on 2009-04-25
Hi

I am having an issue with my video cards fan, it seems to be running very frequently.

The video cards fan is constantly spinning and it goes into really high speeds every three to four minutes.

It seems like this isnt normal because it does the same thing even when the montior is in sleep mode.

Is this normal?? Or is there a way to control this.

ATI-FireGL 7300 in an IBM Z-pro

---

### Post by 3rdalbum on 2009-04-25
The video card itself chooses the speed to run the fan at. You could try updating your video card driver, if there is an update; that might help.

---

### Post by aas452 on 2009-04-25
looks like I updated the new ubuntu 9 and the problem was solved the fan doesn't seem to be spining as frequentlly

---

### Post by aas452 on 2009-04-25
Looks like the Jaunty deleted my ati driver and I am getting an error on reinstall

```

root@VOXEL:/home/angelo/Desktop/fglrx-8.583# source ati-driver-installer-8.583-x86.x86_64.run

Created directory fglrx-install.ZpkFyy

Verifying archive integrity...head: cannot open `bash' for reading: No such file or directory

Error in MD5 checksums: d41d8cd98f00b204e9800998ecf8427e is different from 1968cfec45c5d7e1b3895a782a34d032


```

Is the installer not reading the bash shell??

---

### Post by peakshysteria on 2009-04-25
[Ubuntu Jaunty Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide") might help you. I'm currently not in need of the ATI driver myself. My system works very well out of the box. The Installation Guide helped me installing the driver on previous Ubuntu versions with great success.

---

### Post by aas452 on 2009-04-25
Yea tried that but getting an error on the restart, before X loads

Here is the message

> The following error was encountered. You need to update your configuaration to solve this.

(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so

(EE) Failed to load module "glx" (loader fail, 7)

(EE) Failed to load module "fglrx" (module requirement mismatch,0)

(EE) No driver availiable

Anyone running into the same issue??

Here is my xorg.conf file

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

