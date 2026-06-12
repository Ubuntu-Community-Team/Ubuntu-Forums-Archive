---
title: "microphone doesn't work on my T61 7658rvu"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by stevencxr on 2009-02-01
Hi everyone, i'm a totally newbee linux user >_<

I just installed ubuntu 8.10 on my laptop and seems like my microphone doesn't work in Skype, and i went to skype help site, which is [http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html).
i followed the instruction and it's still not working.
so how could I fix this problem?

thanks!

---

### Post by Crafty Kisses on 2009-02-01
What are the results of this command?
```
lspci
```

---

### Post by stevencxr on 2009-02-01
this is the result of the command, thanks!
xiaoran@xiaoran-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)

---

### Post by stevencxr on 2009-02-01
ok, after reading [http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#Multimedia_Keys](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#Multimedia_Keys)
the mic works on my Sound Record. but still not works on Skype.

there are 4 options in the sound in dropdown list in the Skype Options:
HDA Intel(hw:Intel,0) --works but no playback for the testing call
HDA Intel(plughw:Intel,0) --dowsn't work, "Problem with audio capture"
HDA Intel(hw:Intel,1) --dowsn't work, "Problem with audio capture"
HDA Intel(plughw:Intel,1) --dowsn't work, "Problem with audio capture"

......please...

---

### Post by uchihaitachi on 2009-02-03
I struggled with getting skype to work as well on my t61p.

I couldn't get my laptop mic to work but having plugging in a mic does work for me.

HDA Intel(hw:Intel,0) Only this will work without the time lag delay bug.
Pulse will work but the lag delay bug will hit you.

Poke around in your audio settings to check that your mic aren't mute.

Don't let skype automatically adjust the mixer. They get it wrong sometimes.

I used pulse for sound out and ringing.
ALSA for sound capture.

Hopefully you get yours working. It was hours of trial and error and googling with a patient friend before I got mine working.

---

