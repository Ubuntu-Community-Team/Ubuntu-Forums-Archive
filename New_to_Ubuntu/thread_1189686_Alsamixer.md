---
title: "Alsamixer?"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by seraphim23 on 2009-06-17
this is related to my other posts, but I thought that this would be more recognizable.  When I put in 

> alsamixer[QUOTE]

into the terminal, then I get this 

[QUOTE]alsamixer: function snd_ctl_open failed for default: No such file or directory 

perhaps someone can surmise my sound difficulty from this?

---

### Post by jmszr on 2009-06-17
serphim23,

Have you checked in the Synaptic Package Manager to see if alsamixer is installed?
System > Administration > Synaptic Package Manager > Search:alsamixer. It may be installed by default, I don't know. But it's worth checking.

---

### Post by kpkeerthi on 2009-06-17
> **seraphim23 said:**
> this is related to my other posts, but I thought that this would be more recognizable.  When I put in 

[QUOTE]alsamixer[QUOTE]

into the terminal, then I get this 



perhaps someone can surmise my sound difficulty from this?

This is because Ubuntu has not recognized and configured your sound card. You can't run alsamixer when your sound card is NOT in a working state.

---

### Post by kerry_s on 2009-06-17
post the output of->** lspci | grep audio**

---

### Post by seraphim23 on 2009-06-17
when I put in 

[B] lspci | grep audio

[/B]I got literally nothing as an output, it just went back to the input command line.

---

### Post by seraphim23 on 2009-06-17
[/quote]
This is because Ubuntu has not recognized and configured your sound card. You can't run alsamixer when your sound card is NOT in a working state.[/quote]

ummm how do i get it in a working state then?

---

### Post by kerry_s on 2009-06-17
first we need to know what it is to tell you how to get it working.

try just "**lspci**" it might be reading as "unknown" instead of audio.

---

### Post by seraphim23 on 2009-06-17
> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)


thats the whole out put of **lspl**. as you can see it is detecting the sound card at 14.2 and at 1:05.1 I dont know what do from here though

---

### Post by kerry_s on 2009-06-17
looks like others have dealt with that card before:
[http://ubuntuforums.org/showthread.php?t=1124049](http://ubuntuforums.org/showthread.php?t=1124049)

---

### Post by seraphim23 on 2009-06-17
umm ok, but ive put that line at the bottom of the modprobe.conf file  but it was to no avail
options snd-hda-intel model=dell-m4-2

---

### Post by kerry_s on 2009-06-17
> **seraphim23 said:**
> umm ok, but ive put that line at the bottom of the modprobe.conf file  but it was to no avail
options snd-hda-intel model=dell-m4-2

there's nothing about modprobe.conf, this is what you need to try.

> I edit my /etc/modprobe.d/sound file and put this :
Code:

options snd slots=snd-hda-intel,snd-hda-intel
options snd-hda-intel model=dell-m4-2
# 5Dex.Jpa__qQ4asA:SBx00 Azalia (Intel HDA)
alias snd-card-1 snd-hda-intel
# l4dC.vfAxXUx5zd4:RS780 Azalia controller
alias snd-card-0 snd-hda-intel



---

### Post by seraphim23 on 2009-06-17
Ok well how do I edit that? because I think I did something similar at least...

---

### Post by kerry_s on 2009-06-17
> **seraphim23 said:**
> Ok well how do I edit that? because I think I did something similar at least...

press **alt+f2**
type> **gksudo gedit /etc/modprobe.d/sound**

---

### Post by seraphim23 on 2009-06-17
ok.. I got a blank page for that... well I pasted that code in there and im rebooting, lets see what happens

---

### Post by seraphim23 on 2009-06-17
yeah, that didnt do anything.

---

### Post by meditatingfrog on 2009-06-17
Sup dude,

lspci | grep Audio 

worked for me.  It is case sensitive for me.

---

### Post by meditatingfrog on 2009-06-17
I'm not really sure how the sound works in Ubuntu.  I know there are two software components, PulseAudio, and Alsa.  I THINK there is a push to make PulseAudio the default sound solution, but I could be mistaken.  

This having been said, I'm not sure how PulseAudio gets configured, or Alsa for that matter, or if PulseAudio or Alsa are a collection of device drivers for various sound hardware.  

Now that we know what I DON'T know, I can tell you when I run lspci | grep Audio I get:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

And, when I type top while using xmms2 (for playing music) there is also a pulseaudio program running.  Together both use about 60% of my CPU, which is currently clocked at 800mhz (of 1.47Ghz total).

What happens when you run the tests in Preferences -> Sound?  I'm running Jaunty, btw, and now in Preferences -> Sound I have "PulseAudio Sound Server" as an option, and it is selected.  I didn't notice this in the previous versions of Ubuntu.

---

### Post by kerry_s on 2009-06-17
> **seraphim23 said:**
> ok.. I got a blank page for that... well I pasted that code in there and im rebooting, lets see what happens

i need to see your /var/log/dmesg
**gksudo gedit /var/log/dmesg**

selectall copy & paste here in the code tags(#)

---

### Post by seraphim23 on 2009-06-18
ok well i fixed it.

basically, i had been messing around with the sound and all it need was a simple fix, actually i did a clean of 9.04 again, my speakers didnt work, but the headphones did, from there i did the 

> I edit my /etc/modprobe.d/sound file and put this :
Code:

options snd slots=snd-hda-intel,snd-hda-intel
options snd-hda-intel model=dell-m4-2
# 5Dex.Jpa__qQ4asA:SBx00 Azalia (Intel HDA)
alias snd-card-1 snd-hda-intel
# l4dC.vfAxXUx5zd4:RS780 Azalia controller
alias snd-card-0 snd-hda-intel

and now it  all works :) sorry for being such a pain. there's currently no other troubles that im dealing with.  all the best

---

