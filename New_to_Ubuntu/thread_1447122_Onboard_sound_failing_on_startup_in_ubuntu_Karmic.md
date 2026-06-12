---
title: "Onboard sound failing on startup in ubuntu Karmic"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by gaspros on 2010-04-04
Hi There, I am new to Linux/ubuntu
Having read everything I can on sound issues in ubuntu documentation plus forums and possibly mucked up all my setting multiple times over I am back for some live support if anybody can help out there. 

The onboard sound is recognized as 
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27D8]
bus info: pci@0000:00:1b.0
[FONT=monospace]
It fails on startup with the following error[/FONT][FONT=monospace]
[/FONT]udevd-work [123]       /sbin/modprobe -b pci:v00008086d00002E32sv00001849sd00002E32bc03sc00i00'  unexpected exit with status 0x0009 
[FONT=monospace]
the error in the daemon.log file is
 init: udevtrigger post-stop process (557) terminated with status 1
 udevd[546]: worker [561] unexpectedly returned with status 0x0100
 udevd[546]: worker [561] failed while handling '/devices/pci0000:00/0000:00:1b.0'

When this happens on boot it takes about 3 minutes and then continues to boot into ubuntu without sound working

It is supported hardware by Alsa and here is some information from my PC
from some script that I found in one of the documents:
[http://www.alsa-project.org/db/?f=00c6e7e705a2918107a45669400bb9eed1b032e8](http://www.alsa-project.org/db/?f=00c6e7e705a2918107a45669400bb9eed1b032e8)

sudo aplay -l
aplay: device_list:223: no soundcards found...

find /lib/modules/`uname -r` | grep snd-hda-intel

/lib/modules/2.6.31-20-generic/updates/alsa/snd-hda-intel.ko
/lib/modules/2.6.31-20-generic/kernel/sound/pci/hda/snd-hda-intel.ko

lspci -v | less

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: ASRock Incorporation Device 0397
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at feaf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

The onboard soundcard has worked in the past prior to upgrading to Karmic.

Can anybody help me


[/FONT]

---

### Post by gaspros on 2010-04-05
Found a thread that suggests removing the alsa drivers and re-installing them
So I am trying that now

Result: Made no difference: Same error on boot and no soundcard listed

---

### Post by NightwishFan on 2010-04-05
Try a live CD of Karmic and see if sound works. If so, backup your personal data and do a full re-installation from the CD. If not, I will dig something up to help you. ;)

---

### Post by gaspros on 2010-04-05
Thats the place I got to as well. I think I have tried one to many things and essentially need to do a re-install. I'll get back to you when its done.

---

### Post by gaspros on 2010-04-05
OK so live CD of Karmic has my usual problem of only working if I select safe graphics mode and then it does its thing of dropping out to terminal for 3 minutes and then continuing on and booting up.
But there is no sound with Karmic. Last time sound sucessfully worked was with Jaunty.
I can load up Jaunty if that will help diagnose the problem. I would like to be able to upgrade in the future.

[FONT=monospace]sudo aplay -l
aplay: device_list:223: no soundcards found...

This is in the live CD without doing the full install so far.
[/FONT]

---

### Post by gaspros on 2010-04-05
I did the same with Jaunty 9.04 and it booted fine with the live CD. No need for safe graphics and the sound is working. Drums and clicks away when it loads.

ubuntu@ubuntu:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

So how do I get this to work in Karmic or any future upgrade?

---

### Post by gaspros on 2010-04-05
So in Jaunty everything works fine but I cant upgrade anything for fear of it all stuffing up.

Here is a Jaunty alsa-info.txt which can be compared to the [www.alsa-project.org]("http://www.alsa-project.org") link in the original post

Here it is for convienience:
[http://www.alsa-project.org/db/?f=00c6e7e705a2918107a45669400bb9eed1b032e8](http://www.alsa-project.org/db/?f=00c6e7e705a2918107a45669400bb9eed1b032e8)

Any suggestions other than stay on Jaunty and never upgrade anything ever again?

---

### Post by NightwishFan on 2010-04-05
Try installing this package:
```
sudo aptitude install linux-backports-modules-alsa-karmic-generic
```

Then reboot.

---

### Post by gaspros on 2010-04-06
Thanks for the reply Nightwishfan.
I have already got linux-backports-modules-also-karmic-generic installed  its version 2.6.31.20.33.
I re-installed it anyway just in case.
Rebooted and evrything is the same. 
No soundcard recognised.

---

### Post by gaspros on 2010-04-06
What about the fact that the script run says that the ALSA Version of Driver, Library, and utilities are different.

!!ALSA Version
!!------------
Driver version:     1.0.22.1
Library version:    1.0.20
Utilities version:  1.0.20
I had read somewhere that they should be the same version and they are in Jaunty.

By the way I have created a new partition and loaded up Jaunty into it. So I can now swap between Karmic and Jaunty until I get Karmic working fully. So I am happy to hack away at this.

Can anybody explain what this means or whats failing and what its trying to do.
I think that this is the beginning of the problem.

[FONT=monospace]It fails on startup with the following error[/FONT][FONT=monospace]
[/FONT]udevd-work [123]       /sbin/modprobe -b  pci:v00008086d00002E32sv00001849sd00002E32bc03sc00  i00'  unexpected  exit with status 0x0009 
[FONT=monospace]
[/FONT]

---

### Post by gaspros on 2010-04-06
This also means that I have the alsa-base.conf file from the working Jaunty version available to me as well as any other Jaunty config file that I might need to get this working in Karmic.

Problem is that I dont know enough about linux or ubuntu to know what to do with it.

Anybody got some suggestions for me along these lines?

---

### Post by gaspros on 2010-04-06
I have read through so many posts about this issue -lots talking about configurations and that would probably be really helpful if ubuntu would just be able to regognise the fact that I do actually have a soundcard!!! Why the hell would a newer version of ubuntu fail to do this when the older version does. This has gone on now for weeks!


[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

**Manually Specify Module  Parameters**

 
[LIST]
[*]First you must find which model of sound  card you use, so run this command: 
[/LIST]

cat /proc/asound/card0/codec#* | grep CodecIt will return model of your sound card(s), for  example: "Codec: Realtek ALC260", so your sound card is ALC260.  

No it ****ing doesnt!
There is not even a directory in asound called card0

This is pissing me off big time!

There has to be some guru out there that could look at this and go hey dude all you have to do is this simple little thing and it will all work like it used to.

Help?

---

### Post by NightwishFan on 2010-04-06
Hardware problems happen. I am far from an expert and I contributed as much as I could. I hope you find someone to help you.

---

### Post by gaspros on 2010-04-06
I appreciate your assistance.

---

### Post by NightwishFan on 2010-04-06
Stick with Jaunty for now, it will be supported for a bit still. Try the new Lucid when it is released later this month. If that does not work, I will help you fix then as well. I am sorry I do not know more. I will do research on your chipset for now, hopefully I can get back to you.

---

### Post by gaspros on 2010-04-06
Do you know anything about the modprobe command? It seems to be my first fail.
Do you know what is used in linux to recognise a soundcard ie: alsa or something else?

---

### Post by NightwishFan on 2010-04-06
From what I know modprobe lets you check on the kernel modules for your hardware. I will get back to you, if anything, I am good at digging for solutions.

---

### Post by gaspros on 2010-04-06
Thanks

---

### Post by gaspros on 2010-04-06
Doing something very scary now

[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

Upgrading the alsa using the script mostly because the alsa library and utilities are not the same version in my system as the driver which is the latest version.

---

### Post by NightwishFan on 2010-04-06
Good luck, I hope if works for you.

---

### Post by gaspros on 2010-04-06
After a lengthy download compile and upgrade process I now have the Alsa driver and library and utilities all with the same version

[LIST=1]
[*][COLOR=brown][FONT=monospace]**ALSA Version**[/FONT][/COLOR]
[*]Driver version:     1.0.22.1
[*]Library version:    1.0.22
[*]Utilities version:  1.0.22
[/LIST]
Here is the new link to the "bash alsa-info.sh --pastebin" command

[http://pastebin.ca/1857472](http://pastebin.ca/1857472)

Problem still exists in that modeprobe fails

udevd-work [123] /sbin/modprobe -b pci:v00008086d00002E32sv00001849sd00002E32bc03sc00 i00' unexpected exit with status 0x0009 

The soundcard is not found
aplay -l
aplay: device_list:223: no soundcards found...

---

