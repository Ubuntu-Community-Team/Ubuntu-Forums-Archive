---
title: "Poor sound quality in karmic"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by Wisey on 2009-12-17
Whenever I play songs, the audio sounds scratchy. I tried opening the same file with different players, but the audio quality still remains the same. 
I didn't have this problem in Hardy, I have been looking around for solutions on the net, but I don't know if any of them pertain to this problem and don't want to mess up an otherwise fine system.

---

### Post by lotharmat on 2009-12-17
Could be to do with Pulseaudio

There is a thread on this board somewhere that goes into great detail about how to safely remove pulseaudio and replace it with ALSA


[Here it is]("http://ubuntuforums.org/showthread.php?t=1313253&highlight=safely")

---

### Post by Wisey on 2009-12-18
Thank you for the reply, but I followed all those instructions and the sound is still really scratchy. Any other suggestions?

---

### Post by cgb on 2009-12-18
Not entirely sure if this is the same problem or not since I am using Jaunty but I have a similar issue.  It appears to be an audio gain issue in which if you turn down the volume meter for your audio program to around 70% or 60% it seems to correct the issue.  If you actually watch the volume meter when playing tracks, at least with my issue, you will notice that the meter tops out at 100% when the sound starts distorting.  If you reduce the internal volume it keeps the meter from toping out and keeps it from distorting.

---

### Post by jerrrys on 2009-12-18
i had background noise until i turned down the mix volume

---

### Post by lavinog on 2009-12-18
karmic tried to enable some power saving features of sound cards, but it resulted in popping and scratching noises.

what sound card do you have?:
open a terminal and enter this:
```

lshw -c sound;lspci

```
post what you get here.

also post this:
```

grep 'power_save' /etc/modprobe.d/alsa-base.conf

```

---

### Post by Wisey on 2009-12-19
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:17 memory:ffa7f800-ffa7f9ff memory:ffa7f400-ffa7f4ff
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

And

options snd-hda-intel power_save=10 power_save_controller=N


Kind of amazing though. Turning down the volume really helped. Now the sound is entirely clear. Thank you for the suggestion. 
Is there any complete solution for this problem though?

---

### Post by whitethorn on 2009-12-19
I found when I turn down the PCM value to about -3db in (in terminal) alsamixer.

---

### Post by joes7 on 2009-12-19
Are you sure that your sound card is being recognized?

---

### Post by jerrrys on 2009-12-19
just throwing this out here

[http://ubuntuforums.org/showthread.php?p=8526093#post8526093](http://ubuntuforums.org/showthread.php?p=8526093#post8526093)

---

### Post by lavinog on 2009-12-20
> **joes7 said:**
> Are you sure that your sound card is being recognized?

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
```
looks like it.

---

### Post by Wisey on 2009-12-21
> **jerrrys said:**
> just throwing this out here

[http://ubuntuforums.org/showthread.php?p=8526093#post8526093](http://ubuntuforums.org/showthread.php?p=8526093#post8526093)

I don't whether using audacious fixed it, but the sound is clear right now, and I like the player. Thank you.

---

