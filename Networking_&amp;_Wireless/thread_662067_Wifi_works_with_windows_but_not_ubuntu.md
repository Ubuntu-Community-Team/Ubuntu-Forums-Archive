---
title: "Wifi works with windows but not ubuntu"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by tagno25 on 2008-01-08
I can access my home wifi which has encryption and mac filtering fine in linux and windows, but at my school I can only use windows to access the wifi (they have no encryption, but do have mac filtering on the dhcp server)

my postings may be slow because I must boot into windows to get online

---

### Post by reckless2k2 on 2008-01-08
they may issue an IP at your school based on hostname. i had something similar at old job. make sure your ubuntu hostname matches your windows hostname. 

can you see the school net when you scan?

---

### Post by tagno25 on 2008-01-08
yes I can see the AP when I scan with "iwlist eth1 scan" and network manager can see it.

Will try changing the hostname on Ubuntu to the windows one

****edit****
I changed the hostname logged out then back in and nothing

---

### Post by reckless2k2 on 2008-01-09
do you have your home wifi "hard-coded" in the interfaces file? it should be a simple selection of the school's broadcasting network and that's it. sounds like your wifi is still looking for your home network and won't connect to an open network. there is a roaming enabled button in the network manager and others have chosen to install a better tool like wcid rather than using the network manager. you may want to dabble with both of those.

---

### Post by tagno25 on 2008-01-09
> **reckless2k2 said:**
> do you have your home wifi "hard-coded" in the interfaces file? it should be a simple selection of the school's broadcasting network and that's it. sounds like your wifi is still looking for your home network and won't connect to an open network. there is a roaming enabled button in the network manager and others have chosen to install a better tool like wcid rather than using the network manager. you may want to dabble with both of those.

I can connect to any other network open network. It is actually connecting to my school, but I just do not receive a dhcp lease, but under windows I do.

---

### Post by reckless2k2 on 2008-01-09
sorry tagno25, it sounds like an usual circumstance. i'm not sure i know what could be causing it. 

you could always try to install wicd or use a static IP to see if that works. 

sorry i couldn't be of more help.

---

### Post by dylan1055 on 2008-02-03
yep i have the same problem,

i tried two linux distros and two wifi cards.....  i cant get linux to work on a wep network. (school network)

but interestingly, when i run netstumbler in windows i see a strong signal, and when i refresh wicd in linux i get a week signal . 

dont know if this means anything to anyone, but pls help i hate XP.

i also tried to connect to the same network using a wrt54g flashed with linux and it connects but cant get a ip from dhcp.

---

