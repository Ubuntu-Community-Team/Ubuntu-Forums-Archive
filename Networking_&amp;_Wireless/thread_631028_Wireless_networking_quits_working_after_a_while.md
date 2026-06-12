---
title: "Wireless networking quits working after a while"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by darrylmcginnis on 2007-12-04
It seems that several people have various flavors of networking that quits working after a while.  In my situation, it is wireless with a Belkin Wireless G USB Network Adapter.  When it works, it works GREAT! ...but when it quits, the nm-applet continues to show bars as though it is still connected.  The device can be unplugged and the nm-applet continues to report a connection.  I've tried numerous ways to restart networking to no avail.  It seems that when it fails it actually is the entire USB bus that goes down -- I say this because after the problem manifests itself, the system will not recognize a USB drive being plugged in.  I have also been able to see (by switching to another tty session) a couple of errors that continually repeat themselves:
[ xxxx.xxxxxx] zd1211rw 1-3:1.0: zd_chip_control_leds error -19
and
[ xxxx.xxxxxx] zd1211rw 1-3:1.0: error ioread32 (CR_REG1): -19
where xxxx.xxxxxx are increasing numbers.  Generally, each message comes in groups of 6 to 10 repeats then the other message has several repeats then back to the first, etc. etc.
The only way to get networking to function again is to reboot.
I am running 7.10 (Gutsy) as a fresh install.
Anybody have some info for me?
Darryl

---

### Post by darrylmcginnis on 2007-12-05
bump

---

### Post by GSF1200S on 2007-12-05
> **darrylmcginnis said:**
> bump

I might suggest posting a similar topic in General Help. I wouldnt focus on the wireless card- but definitely bring up how the wireless card works and fails **just as other USB devices do**so that people have that information to help you..

If you focus on the wireless card in the topic, the admins will move it here, or close the thread marking it as a duplicate. I know youre problem impedes your wireless card, but this is actually a USB problem (one ive never seen before).

good luck :)

---

