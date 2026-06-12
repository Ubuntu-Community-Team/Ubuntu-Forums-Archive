---
title: "Dell issu with Ubuntu and Kubuntu 9.04"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by rmaurice on 2009-05-04
I have been a fan of Ubuntu for several years and have introduced many people to this distro. I was somewhat shocked when I couldn't get Ubuntu or Kubuntu 9.04 to run on my computer. The software installs fine but then things work slow and intermitently. Firefox took anywhere from 18 to 90 seconds to start, web pages didn't open (one showed it was loading for 8 hours), software updates didn't download, applications were slow to launch (10 to 30 seconds). I tryed multiple ISO downloads and multiple installs with the same results. Some forums mention ATI issues but my troubles went way beyond those reported issues. I have since installed another OS which is working fine. 
I tried to run this on a Dell Dimension E510 with dual 2.8 GHZ processors and 3 gig of memory, Monitor is Dell 2007FP, Ethernet interface 82801G (1CH7 Family) LAN Controller. The system also has an ACX 100 22Mbps Wireless Interface.

---

### Post by zeroseven0183 on 2009-05-05
I wonder why you're having troubles running Ubuntu with that kind of laptop specs.

Was that a fresh install? Perhaps you may try performing hardware checks on your machine.

... very unusual

---

### Post by Durden on 2009-05-05
Your firefox issue might simply be IPv6. Type "about:config" in the URL bar without the "". Then search for "ipv6" again without the ""

Set it to true (should already be at false). This sped mine up a ton. I never had this issue pre-8.10.

You may also want to disable ipv6 at the system level. I did this also but I've since forgotten how. Perhaps someone here can clue us in.

The only other problem I've had has been with PulseAudio. I wish there was a clean simple way of going back to the audio sub-system of the 7.XX distro.

---

