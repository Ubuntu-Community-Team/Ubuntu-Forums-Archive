---
title: "Ubuntu 8.10 - updated system lost Wlan"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by Danorge on 2008-11-11
hey there i'm new to Ubuntu. 
First of, i bouth a Acer aspire one (8GB - 512mb ram / 8,9" ) a while ago i was not happy with the pre installed OS. 

So i downloaded the Ubuntu 8.10 and installed it via USB. 
After i made the installation, i was not able to go online, i read a topic about how to disable the default driver and this made my Wlan work for a while. 

Now i cant go online. I made a system update with 168 files. 

can anyone point me where to read about my problem, or is there a friendly soul out there that would like to explain it to me :) 

thanks in advance from danorge

---

### Post by Aditu on 2008-11-11
Yes, an answer would be great because I have the same problem :-(

---

### Post by Danorge on 2008-11-12
> To activate ath5k, deactivate the proprietary driver "Atheros wireless card" (System -> Administration -> Hardware Drivers) that Ubuntu tries to use and install the package "linux-backports-modules-intrepid"

sudo aptitude install linux-backports-modules-intrepid

Wireless will work after a reboot.

I am deliberately omitting all other instructions as I hope that ath5k works for all of you as well as for me. 

i have try'ed to follow these intructions but i still cant have a working wlan.

any help is would be great :)

---

### Post by Danorge on 2008-11-13
hmm.

okay what i'm about to do is 

1 re-install ubuntu 8.10 
2 de-activate the defualt driver "Atheros wireless card"
3 reboot
4 No system updates !
5 Wait until some that have done system updates and got them to work properly with the  [COLOR="Red"]Acer aspire one [/COLOR]

Any help would be appreciated.

---

### Post by Danorge on 2008-11-30
wow ubuntu help is like windows support... hope to get some when people care ... over 200 views no answers .. 

thanks for helping a newbie not sure ubuntu is for me after all. back to the good old unreliable windows

---

