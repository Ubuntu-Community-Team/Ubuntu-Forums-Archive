---
title: "Sound and other drivers for HP pavillion tx2635"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by amol_deshmukh on 2009-01-14
Hello,
I have installed Ubuntu 8.10 on my laptop HP pavillion tx2635 tablet PC. I am having some problems configuring the drivers required for this laptop,

1) I have installed ALSA, but still no sound ( Sound card: Realtek ALC268 )
2) No idea how to get touch screen working? (Wacom)

If anyone can guide me then it would be great, thank you

---

### Post by Michael.Godawski on 2009-01-14
hi,

have a look at these guides and report back when you hit the wall or need further help:

[LIST]
[*][https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[*][https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
[/LIST]

---

### Post by Favux on 2009-01-14
Hi amol_deshmukh,

Try the first two posts at this link:

[http://ubuntuforums.org/showthread.php?t=972552&highlight=sound]("http://ubuntuforums.org/showthread.php?t=972552&highlight=sound")

Be sure to search forums for TX2500, there are several helpful threads.

To get the Tablet PC features working you need to install the linuxwacom kernel driver.  Either see Loic2's wiki's (link in following) or if that fails try:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

Then to get rotation so you have a tablet go to:

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

Hope this helps.

---

### Post by oznozz on 2009-01-20
Hi.  I installed 8.10 intrepid on a tx2635 and have the same set of problems.

(1) wacom tablet -- I am going to get back to this.  I have things to try prior to requesting further help.

(2) sound -- the sound issue confounds me.  Here's what we have :

== Conventions ==

== Major Section ==

------------   minor section

............   casual seperator

I will try to make it obvious what each of these sections addresses.



== SOUND ==

-----------------

adding options to alsa-base

I tried adding the following options at the end of /etc/modprobe.d/alsa-base :

options snd-hda-intel model=hp
options snd-hda-intel index=0 model=toshiba
options snd-hda-intel index=0 model=hp

as per, e.g.
[http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm)
[http://ubuntuforums.org/archive/index.php/t-972552.html](http://ubuntuforums.org/archive/index.php/t-972552.html)

I only added 1 option at a time and restarted the sound server with 
$ sudo /etc/init.d/alsa-utils restart
or, I performed a complete restart of the system.

This has *not* resulted in success.

I have tried listening to sound from the headphones and from the built in speakers to no avail.

--------------

Sound Trobuleshooting guide

I tried some of the steps in one of the guides suggested by one of the other posters : 

Sound Troubleshooting
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

The Sound Troubleshooting guide lacks an appropriate amount of nuance for this problem.  The card is detected, but no sound comes out.  [http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm) and other suggest that the machine perceives a mute button constantly pressed down, and the option adding in the first section is supposed to solve that problem.

Here are the results of some of those tests on my machine :

.................

:~$ uname -a
Linux ranaroja 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

..................

:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
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
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

..................

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

..................

:~$ lsusb
Bus 007 Device 003: ID 056a:0093 Wacom Co., Ltd 
Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a104 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

..................

$ find /lib/modules/`uname -r` | grep snd
results in a lot of results.  I won't post them unless asked.

..................

$ sudo lspci -v 

...
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: Hewlett-Packard Company Device 30f1
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
...

------------------

$ killall pulseaudio
$ sudo killall pulseaudio

Killing pulseaudio did not help, although more controls appear in the terminal version of alsamixer.

----------------

System -> Preferences -> Sound

I tried many different settings in to no avail.

----------------

$ alsamixer

when pulseaudio is alive and well, alsamixer shows off 2 master controls, one for output and one for input and it seems that the alsamixer is connected to the pulseaudio virtual device.

when pulseaudio is killed, other mixer options appear; there are about 12 total.

----------------

Muting is not an obvious problem.  The mute button on the keyboard pops up a mute/unmute box in the X GUI.  The alsamixer program in the terminal reflects the mute button's activity.  This holds true for all the visible channels in alsamixer when puleaudio is killed and I select the different channels using sound preferences.  It does not change the control panel's status.  I don't know what that means.

=======

Any ideas?

Thanks,
oznozz

If I figure anything out hacking away at this, I'll post some things.

---

### Post by oznozz on 2009-01-20
Someone suggested adding 
acpi=off 
on another forum to the kernel boot options.

Adding that bit and restarting disabled at least the wifi card and did nothing to help the sound situation.

So, I don't think that is an option.

As a side note, turning off acpi caused /proc/cpuinfo to report 1 processor at the maximum MHz, whereas now /proc/cpuinfo reports two CPUs running at around 600 MHz each.  I have yet to test whether this means acpi is working correctly or not.

---

### Post by Favux on 2009-01-20
Hi Oznozz,

As I suggested above please go to:

[http://ubuntuforums.org/showthread.php?t=972552&highlight=sound]("http://ubuntuforums.org/showthread.php?t=972552&highlight=sound")

And read the first two posts.

Mirosol's HOW TO was very useful for us TX2000 owners. I'm glad you found it.  The line you are looking for is most likely:
```
options snd-hda-intel index=0 model=toshiba position_fix=1
```
Be sure to right-click the volume control icon (little speaker) and turn up the volume sliders (including PCM).

I do not think, with the Intrepid kernels, there is any utility for "acpi=off".  Maybe a TX2500 owner could chime in.

Good luck!

---

### Post by kansasnoob on 2009-01-20
Since it's Realtek you need to adjust all of the VIA outputs.

I like to install gnome-alsamixer either from Synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video. Pay special attention to the first three toggles and all the VIA toggles (the last 4). Also whether you have an external amp or not.

I like gnome-alsamixer because it puts all the options in front of me. Sometimes options I hadn't thought of.

---

### Post by kansasnoob on 2009-01-20
If it's a Pulse-Audio problem start here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I actually doubt it with 8.10.

---

### Post by oznozz on 2009-01-20
Favux :  Thank you for your quick response.  Your suggested modification to the config file works; my system now produces sound from both the headphones and the speakers.

Can anybody provide or point to an explanation of why this works?

I ask because it seems that the exact line Favux recommends must be added to the correct configuration file and then the entire computer must be restarted or else the fix doesn't work.

I tried restarting alsa with a
$ sudo /etc/init.d/alsa-utils restart
which reported something like :
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
I was unable to play sounds after this.  I had to restart to see an effect.

I also tried the following alternative lines :

options snd-hda-intel index=0  position_fix=1
options snd-hda-intel index=0 model=hp  position_fix=1

Neither of these result in sound.  From the previous post, it is plain that eliminating the position_fix=1 component does not work either.

It is a complete mystery to me as to why the recommended fix works, since as far as I know, HP and Toshiba are not the same company, and there is nothing in the configuration info I posted which would suggest that toshiba makes even a bit of sense as a model for any component of this machine.  Hopefully, I'm missing something.


Kansanoob : I tried installing gnome-alsamixer before I tried adding what appears to be an inappropriately-parameterized line to a kernel module configuration file, but it didn't help.

---

### Post by Favux on 2009-01-21
Hi oznozz,

We would have to ask gali98 how he came up with the fix.  I think I dimly remember him talking about an extensive search he had done when he first posted the fix.  I don't remember where that was.  Unfortunately he has not posted in a couple of months.

---

