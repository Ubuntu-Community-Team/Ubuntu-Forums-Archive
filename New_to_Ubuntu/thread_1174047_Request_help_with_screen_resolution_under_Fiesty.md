---
title: "Request help with screen resolution under Fiesty"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by m9ke on 2009-05-30
Could anyone offer suggestions as to what I might do to get more resolution out of my monitor?  Currently under Ubuntu Fiesty Fawn it won't offer any options higher than 1024x768.

I know the monitor hardware is capable of higher resolution settings that what I am seeing from my Ubuntu box because I have the same monitor connected to a windows box via a KVM switch and it offers higher resolutions under Windows XP.

I am running an unsupported version of Ubuntu, Fiesty Fawn.  I installed it long ago, and spent a lot of time getting it working perfectly for everything I want to do.  This screen resolution issue is an irritation I have been living with until now.  If I can fix it with out the major surgery of a clean reinstall, I will do so. 

Details: 
In System: Preferences: 
Screen Resolution: only options offered 1024x768, 800x600, or 640x480
Refresh Rate: 60 Hz is only option offered.

Software:
OS: Ubuntu Fiesty Fawn
Driver(s): 
A search on 'nVidia' in Synaptic package manager on my system shows the following are installed:
--nVidia Accelerated Graphics driver (disabled) 
--linux-restricted-modules-2.6.20-15-generic
--linux-restricted-modules-2.6.20-16-generic
--linux-restricted-modules-2.6.20-17-generic
--nVidia-glx
--nVidia-kernel-common
--restricted-manager
--sensors-applet
--smart-dimmer
--xserver-xorg-video-nv

Hardware:
Graphics card: ASUS N6200/TD/128 GeForce 6200 128MB 64-bit DDR AGP 4X/8X 
Monitor:  NEC MultiSyncy LCD 1700V
Computer itself is an old no-name unit brought back to useful life by Ubuntu!

Any suggestions would be greatly appreciated!
m9ke

---

### Post by Rocket2DMn on 2009-05-30
Since Ubuntu 7.04 is no longer supported, you really should upgrade to a supported version of Ubuntu.  I suggest the latest, which is 9.04 "Jaunty Jackalope".  A lot of improvements have been made in hardware support in the last few years, especially with the X server and restricted video drivers.  You can try out using a LiveCD to make sure your hardware is detected before installing.  An actual install will probably yield better results though.
Of course a fresh install wipes over your existing partitions, so you would need to back everything up first.  Most LCD monitors don't do more than 60hz, so I'm not sure Ubuntu will let you go higher (like 75hz), but you should at least be able to get better screen resolution.

---

### Post by m9ke on 2009-06-02
Thanks, Rocket2DMn!

The upgrade question now becomes moot b/c my boot drive has failed.  Luckily home is on a different physical drive.

Again thanks for your reply!

m9ke

---

### Post by m9ke on 2009-06-02
Manually adding 'Solved' to thread title.  I thought there was a button for that in the Tools menu but can't seem to find it.

---

### Post by Rocket2DMn on 2009-06-02
This is why you can't find the [SOLVED] tool - [http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

Cheers.

---

### Post by m9ke on 2009-06-02
Thanks Rocket2Dmn!  I didn't know that tool went away, but I read the link and get why.

BTW the upgrade to Jaunty went flawlessly.  I installed a new internal HD and power supply while I was at it.

You are quite right, the diff btwn Fiesty and Jaunty is quite pleasing!

Cheers,
m9ke

---

