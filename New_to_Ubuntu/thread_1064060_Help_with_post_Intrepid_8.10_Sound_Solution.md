---
title: "Help with post: Intrepid 8.10 Sound Solution"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by skootar on 2009-02-08
I refer to these instructions and assume they are correct:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

I have managed to install the prerequisites as instructed in the post.

I am stuck at the line "If any of the above is giving you problems, try rebooting." I have rebooted, cycled ac power. There are no devices listed in the Pulse Audio Device Chooser. That's as far as I have been able to get. Everything looked good up to that point. I don't know which sound device to choose in the sound preferences for "Default Mixer Tracks". There are 2 choices: oss and alsa. The instructions don't say which one to choose -- it doesn't matter -- neither resolve problem.

(Before I started with these instructions, sound was only working in a cases: desktop drum sound at login, and using oss sound in xmms. No sound in flash 10 video.)

All I want at this point is for flash video audio to work. It's a lot of work to set this up?

---

### Post by houstonbofh on 2009-02-08
Yes.  No.  Maybe?

First, you have a hardware problem and have given us absolutely no information that we need to solve it.  I recommend abandoning this thread, and starting a new one.  In that pick the title "Gigabyte GA-123 motherboard - No Audio" or whatever motherboard and system you have.  You can also search for the same...  When you post, give details.  If you can open a terminal, post the output of 'lspci' as well.  You will get a better and faster response that way.

---

### Post by skootar on 2009-02-08
Since I had the drum sound I reasonably assumed it was a software problem.
 
There are 12 choices for output device in sound preferences. Only oss sound plays the test tone.

I have a turtle beach santa cruz sound card on an abit kr7a motherboard.


00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0b.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0d.0 SCSI storage controller: Adaptec AHA-2940U/UW/D / AIC-7881U
00:0f.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:13.0 RAID bus controller: HighPoint Technologies, Inc. HPT366/368/370/370A/372/372N (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]

---

### Post by skootar on 2009-02-08
It's a software problem. 

I just got it working using magic here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

See the section:

Part C: Intrepid Ibex (8.10)

---

### Post by houstonbofh on 2009-02-09
Missed that...  Sorry, but usually no choices in the mixer is a hardware detection problem.  Glad you got it sorted!

---

