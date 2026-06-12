---
title: "[SOLVED] Media Freezes Computer"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by RealG187 on 2008-12-30
When ever I open Totem player is freezes my computer. Whether I open audio or video it does it, VLC did it for video, not sure about audio.

Rhythmbox doesn't do it.

What happens it the audio keeps playing but the video is just black, I can move my cursor but not click.

I think this happened when I played the "experience ubuntu.ogg" video file as a test too, that was before I installed the extra plugins.

---

### Post by Jengajam2 on 2008-12-30
Make sure you have gstreamer and the "good" plugin set reinstalled via synaptic, then try it again.

---

### Post by RealG187 on 2008-12-30
I use "apt-get install whatever"

I typed in "sudo apt-get install ubuntu-restricted-extras" to originally install the plugins.

---

### Post by Hydrid on 2008-12-30
Something is wrong with your video codecs unistall them and install them again,do the same for your VGA.

---

### Post by RealG187 on 2008-12-30
would I go

```

sudo apt-get remove ubuntu-restricted-extras
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by RealG187 on 2008-12-30
Okay VLC doesn't do it for audio.

So:

**[color=green]Player[/color] -  [color=blue]Audio Freezes[/color] - [color=red]Video Freezes[/color]**
[color=green]VLC[/color] - [color=blue]No[/color] - [color=red]Yes[/color]
[color=green]Totem[/color] - [color=blue]Yes[/color] - [color=red]Yes[/color]
[color=green]Rhythmxbox[/color] - [color=blue]No[/color] - [color=red]N/A[/color]

---

### Post by RealG187 on 2008-12-30
I reinstalled the plugins and in the process had to uninstall all my media players except VLC. I reinstalled totem and it still does it...

---

### Post by RealG187 on 2008-12-31
It does this for my webcam too. Could it be something with my video card? (I will find out what it is when I boot back into Windows)

UPDATE: It's Mobile Intel(R) 4 Series Express Chipset Family

---

### Post by Coder543 on 2009-01-01
Make sure you are using the latest ubuntu.
If you are, you might attempt to reinstall it, that has worked wonders for me in my installing ubuntu on various hardware setups. Sometimes your install really is messed up. If you don't want to do that, then don't do it. That is just what has worked for me.

---

### Post by handydan918 on 2009-01-01
> **RealG187 said:**
> It does this for my webcam too. Could it be something with my video card? (I will find out what it is when I boot back into Windows)

UPDATE: It's Mobile Intel(R) 4 Series Express Chipset Family

Yeah, sometimes cutting edge hardware (and drivers) cause issues. Maybe you coould post the output of ```
lspci
```so we can see what the system is seeing the hardware as.

---

### Post by RealG187 on 2009-01-02
mpg@MIKED6:~$ lspci
00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
mpg@MIKED6:~$

---

### Post by Tomatz on 2009-01-06
I have fixed the issue for someone here:

[http://ubuntuforums.org/showthread.php?t=1011168&page=3](http://ubuntuforums.org/showthread.php?t=1011168&page=3)

---

### Post by rampageoberon on 2009-01-06
I'm getting the very same problem. It is quite temperamental, videos seem to work at times and at times they don't. I'll try the steps given in the linked post and see if it helps.

On the topic I posted I got the following advice (not sure if it works as yet but my system hasn't crashed in one attempt)

[http://ubuntuforums.org/showthread.php?t=807443](http://ubuntuforums.org/showthread.php?t=807443)

---

### Post by RealG187 on 2009-01-10
I uprgaded to 8.10 and it worked, 8.10 probably uses X11 by default.

---

