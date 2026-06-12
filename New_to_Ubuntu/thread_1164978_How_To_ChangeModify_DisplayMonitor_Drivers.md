---
title: "How To Change/Modify Display/Monitor Drivers?"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by matey3 on 2009-05-20
how to I tell it what kind of monitor i have?

I cannot find it anywhere in 9.04?

the hardware section is empty, the display setting is also empty but it says the monitor is UNKNOWN!
with 8.04 i changed my unknown monitor to Acer flat screen and then I got high resolution. why cant I do the same in jaunty?


thanks

---

### Post by halitech on 2009-05-20
most of the settings are now down 'automagically' and the xorg.conf file is pretty much ignored. can you post the output of 
```
cat /etc/X11/xorg.conf
```
also what video card do you have?

---

### Post by matey3 on 2009-05-20
thanks for the reply,
I think I have nVidia card in here but the xorg file is different now, it used to hold more info.and detail;


# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
EndSection

---

### Post by halitech on 2009-05-20
that looks about right with the settings being taken care of without needing to hardcode things anymore. You say you have an Nvidia card, what model and have you installed the hardware drivers for it?

```
lspci -C video
``` will give us details about the card

---

### Post by matey3 on 2009-05-20
strange, cuz it does not like C or video in the command line?
so i just did a lspci and found out its all SIS onboard stuff:
#
# lspci 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

Thanks!

---

### Post by halitech on 2009-05-20
sorry, got my commands mixed up, was thinking lshw -c video

SiS is notoriously bad for getting video to work well. what resolution do you have currently?

---

### Post by matey3 on 2009-05-20
yeah I thought so...

i have like up to 1024x768 but last time I had it up to 1280 x 1080? by telling 8.04 I had a flat Acer monitor. I did not have to change my video card settings just the monitor and it gave me a decent res.
now I cant change it (anything) with 9.04, it is just annoying as hekk.

thanks for your help

---

### Post by halitech on 2009-05-20
I'm not sure exactly what to put in for the xorg settings that would help you out, sorry.

---

### Post by matey3 on 2009-05-20
thats OK, thanks for taking your time.

regards;

---

### Post by CatKiller on 2009-05-20
> **matey3 said:**
> how to I tell it what kind of monitor i have?

I cannot find it anywhere in 9.04?

The tool was taken out because it wasn't very robust. I understand that it will come back when it's been re-written.

In the meantime, the values you are probably most interested in are the VertRefresh and HorizSync ranges, which you can probably get from your monitor's manual. They go in the "Monitor" Section of your xorg.conf, like so:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```

---

