---
title: "Graphics driver produces Karmic chaos"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by nnjond on 2009-11-04
Hi,

This is my xorg.conf. It yealds a tollerable display for the  mean-time.

nnjond@den-desktop:~$ cat /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"vesa"
	Option	"NoLogo"	"True"
EndSection


The Ubuntu app,'Hardware drivers' recommends i install Nvidia 173

I believe i purged my sys by;

 sudo apt-get --purge remove nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings 

nnjond@nnjond-desktop:~$ dpkg -l | grep nvidia 

and

sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}') 

I then rebooted and installed the recommended Nvidia 173, then rebooted. It wouldn't load. grub revealed the one change in xorg.conf:


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


Can anyone see my problem?

---

### Post by bawilson2 on 2009-11-12
Out of curiosity what is the chip set your video is using?

Trying running the following if you're not sure.

```

sudo lshw -C video

```

and 
```

lspci

```

---

