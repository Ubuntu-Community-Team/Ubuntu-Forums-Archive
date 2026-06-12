---
title: "need help with finding wifi networks"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by steve19137 on 2009-12-04
i have had ubuntu running at suburb quaility for a few weeks now, after i was left ubuntu because if a hardware issue, but im back! the wait was overdue. anyway back OT, i have macmini, and i upgraded its hard drive from 120GBs to 360GBs. the mac is fine, im just telling the story. this left me with a 120GB drive ad nothing to do with it. the laptop that has ubuntu running came with an 80GB HD, a factory standard, strangely enough. so when i was using vista, i wanted to mave the drives from the 80GB to the 120GB. it didnt work because it was originally a mac hard drive. so i thought i would scrap windows, and hit up ubunut. got that done. so i got 9.10 on my 120 hard drive, not surprising, considering the versatility of ubuntu. now i want to connect to my wifi, and i cant. i have an airport express with WEP 40BIT encryption, and i know the hex password that i can enter if needed. but when i click on the wifi dongle thingy, i only see wired networks. and its irritating, because i bring this laptop to school. if there is something to enter into terminal, i can do that, i have a exponentially growing knowledge of ubuntu terminal, so terminal is no isssue whatsoever. please help asap.

---

### Post by Greenwidth on 2009-12-04
Sounds like Ubuntu might not have picked up your wifi adapter driver, do you have one you can enable in:
System > Admin > Hardware Drivers

If not, type lspci into terminal to find out what card you have, post back for card specific help.

---

### Post by sgosnell on 2009-12-04
Did you turn the wifi radio on?

---

### Post by bluesscream on 2009-12-04
try wicd

---

### Post by steve19137 on 2009-12-05
i figured out the issue. i had put in my new 120gb drive and went straight to 9.10. well, as it turns out, you can only get my wifi driver if you install 8.10, then update to 9.10, or unless you update sources after installation of 9.10. so i updated stuff, and it still wouldnt register. no wifi radio button under the right click menu of the net work applet, nothing. so being very frustrated, i went to 8.10, then upgraded (very slowly). now i have my 120gb drive with perfect wifi. also, why was my update so slow? i was hard wired when i updated, very strange to me. is ubuntu so popular that its killing the servers?

---

