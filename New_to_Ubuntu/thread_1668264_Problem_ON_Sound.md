---
title: "Problem ON Sound"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by GhOsT un1T on 2011-01-16
Hey Guys.

I have installed ubuntu 10.04 

And my sound is not working since then.
can someone help me ?

---

### Post by mastablasta on 2011-01-16
what sound card do you have?
Open terminal (accessories->terminal) and type in this command and pos the output:

```
lspci
```

This will list your PCI devices.


Also have a look at this guide to porpperly troubleshoot your nonworking sound:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by GhOsT un1T on 2011-01-16
> **mastablasta said:**
> what sound card do you have?
Open terminal (accessories->terminal) and type in this command and pos the output:

```
lspci
```This will list your PCI devices.


Also have a look at this guide to porpperly troubleshoot your nonworking sound:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


Here it is bro

```
00:00.0 Host bridge: VIA Technologies, Inc. P4X333/P4X400/PT800 AGP Bridge (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0b.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

---

### Post by [Snc] on 2011-01-16
> **GhOsT un1T said:**
> 00:0b.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
...
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

you have two multimedia controllers, check which one is enabled and used "System"->"Preferences"->"sound" or Alt+F2 and run "gnome-volume-control"

Sound can be a little bit tricky under Linux :)

---

### Post by diablo75 on 2011-01-16
If you click on the little speaker icon in the upper right panel, a little pop-out menu will appear with a master volume slider as well as a button that gives you access to Pulse Audio preferences.  Inside this panel are tabs for selecting output hardware devices and the audio modes you wish to use with them (do you just have a card with 2 output channels or 5.1 or 7.1, etc.).

One other possibility is that a you have a not-so-obvious audio channel muted.  I just installed Ubuntu on a Zotac Mini Mag and the sound didn't work out of the box until I ran ALSA mixer in the terminal and unmuted a channel, as described [here]("http://askubuntu.com/questions/20303/how-do-i-get-hdmi-audio-working-on-a-zotac-mag-hd-nd01-u").

---

