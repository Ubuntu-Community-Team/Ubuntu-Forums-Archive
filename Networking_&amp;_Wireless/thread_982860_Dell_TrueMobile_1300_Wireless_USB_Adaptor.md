---
title: "Dell TrueMobile 1300 Wireless USB Adaptor"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by IBUA on 2008-11-15
Hey,

I'm very very new to Linux and Ubuntu and i installed Ubuntu 8.04 yesterday and was about to update it to Ubuntu Studio until i realised that i had no internet. So i went and tried to get it to work but i think it hasn't picked up my Dell TrueMobile 1300 Wireless USB Adaptor or something. I had a look round on the Documentation and various threads on here but the things i tried didn't make sense (because i'm so new to Linux) and didn't work.

So i'm wondering if anyone could give me a point by point easy to understand (so for noobs/dummys) style on how to set it up then connect to my houses network. (The router is on a different computer to the one with Linux is on)

Thanks for help in advance.



----------------
Now playing: [OOMPH! - (Why I'll never be) clean again](http://www.foxytunes.com/artist/oomph!/track/(why+ill+never+be)+clean+again)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by w2vy on 2009-04-03
The solution is easy for 8.10 (onward)

System->Administration->Hardware Drivers

Just activate the driver!

tom

many thanks to Linux Questions for the answer...

[http://www.linuxquestions.org/questions/showthread.php?p=3348250#post3348250]("http://www.linuxquestions.org/questions/showthread.php?p=3348250#post3348250")

---

### Post by Tsu Do Nym on 2010-05-10
I have this same adapter. In 9.10 it worked properly just by plugging it in. It used the open source drivers and didn't require any proprietary drivers from "hardware drivers". In 10.04, however, it is no longer recognized and no longer works. Bug or new feature?

---

### Post by w2vy on 2010-05-11
On 9.10 I was using the Broadcom B43legacy driver.

I upgraded to 10.0 and I see Broadcom drivers in the software center.

Give them a try

tom

---

### Post by Tsu Do Nym on 2010-05-11
I found that the problem is that in 10.04 you have to install the linux-firmware-nonfree package (the one that says it's for DVB cards). I don't know why, I didn't have to in 9.10. But that's what made it work.

---

