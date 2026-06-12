---
title: "go to fullscreen = reboot?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by crho85 on 2009-02-11
Hi, whenever I try to run a game that starts out in full screen such as supertux, I system takes me back to the log on screen. Does anyone have a solution for this?

System info
glxgears= ave 220 fps
direct render = on
resolution = 1028/720 (or something like that)

---

### Post by Bölvaður on 2009-02-11
> **crho85 said:**
> 
glxgears= ave 220 fps

whow that is amazingly little. What graphical card do you have? (you can find it on the hardwerlist when you type 'lshw' in the terminal)

---

### Post by crho85 on 2009-02-11
lshw:

```
*-display UNCLAIMED
                description: VGA compatible controller
                [B]product: Radeon IGP 320 M
                vendor: ATI Technologies Inc[/B]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=66 mingnt=8
```

That's right... the dreaded IGP 320 Radeon.

It was a struggle just to get desktop effects, the proper resolution, and direct rendering enabled

---

### Post by crho85 on 2009-02-11
bump

---

### Post by lavinog on 2009-02-11
What driver is being used
what ubuntu version/arch?

---

### Post by crho85 on 2009-02-11
> **lavinog said:**
> What driver is being used
what ubuntu version/arch?

This is 8.10 (intrepid)

I am not sure about the driver. So here is xorg.conf and glxinfo vendor
```

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.



Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        SubSection "Display"
               Modes             "1024x768"
        EndSubSection
EndSection
```

---

### Post by Bölvaður on 2009-02-12
sorry for a slow reply.

in your xorg.conf do you find anything like:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"ati"
	Option	"NoLogo"	"True"
EndSection
```

For your card it is supposed to be ati as driver in there, but not vesa which is a basic driver... like a backup (also used in "safe graphical mode)"


The driver can be obtained through he repos, and the package's name is *xserver-xorg-video-ati* but you probably already have it installed. Just make sure it is there when you change xorg.conf to ati. Make sure you **take backup of xorg.conf** as if something isn't like it is supposed to be you may have to repair via live cd or boot under recover mode to replace the new xorg.conf with the old one.

---

### Post by crho85 on 2009-02-17
> **Bölvaður said:**
> sorry for a slow reply.

in your xorg.conf do you find anything like:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"ati"
	Option	"NoLogo"	"True"
EndSection
```

For your card it is supposed to be ati as driver in there, but not vesa which is a basic driver... like a backup (also used in "safe graphical mode)"


I have the ATI driver installed. I tried this xorg.conf but it does not work. I am still getting a log out when I try to open a full screen app. 

would the radeon driver work?

---

