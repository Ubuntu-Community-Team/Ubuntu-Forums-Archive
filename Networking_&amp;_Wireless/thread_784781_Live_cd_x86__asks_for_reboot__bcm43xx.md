---
title: "Live cd x86  asks for reboot  bcm43xx"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by SerpentDrago on 2008-05-06
so i have the  bcm43xx firmware files on a spare drive , and boot into the livecd , it then (detects new hardware) and asks for a reboot. I know how to get it working on a Real install but.. i need it working IN a livecd 

ok this is a LIVE CD , i can't just reboot ..

So..
What .dep packages do i need to put on a spare drive.
and how would i setup this WHILE using the livecd. I can't reboot a livecd

I need networking working so i can do a complicated fakeraid (nvraid) install without trying to modify the install instructions to be networkless

---

### Post by superprash2003 on 2008-05-06
well in linux you hardly have to reboot.. but when its necessary, i think its necessary.. so i think the only way out is to install ubuntu

---

### Post by Ayuthia on 2008-05-06
> **SerpentDrago said:**
> so i have the  bcm43xx firmware files on a spare drive , and boot into the livecd , it then (detects new hardware) and asks for a reboot. I know how to get it working on a Real install but.. i need it working IN a livecd 

ok this is a LIVE CD , i can't just reboot ..

So..
What .dep packages do i need to put on a spare drive.
and how would i setup this WHILE using the livecd. I can't reboot a livecd

I need networking working so i can do a complicated fakeraid (nvraid) install without trying to modify the install instructions to be networkless
When you say that it then detects new hardware and asks for a reboot, are you saying that you enabled the wireless on the livecd and then it asks for a reboot?  You also say bcm43xx, which version of Ubuntu are you using?

---

### Post by SerpentDrago on 2008-05-07
Solved the Issue , found another post that walked me through manual firmware install with fwcutter.

Thanks

---

