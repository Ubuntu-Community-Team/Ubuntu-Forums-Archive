---
title: "download speed"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by ettercap on 2008-06-19
hello every 1

i use sudo pppoeconf for my broadband internet access where i type my 
ISP's user name and password .
the problem is

when i download through mozilla i get a good speed around
120-200(KBPS) as i hav a 2 Mbps connection

whereas when i download through synaptic package manager 
the speed is like 20-30kBPS
some times it falls below 1KBPS !!!!!!

is there any problem......or do i hav to set maximum speed somewhere...

plz help.........

---

### Post by SpaceTeddy on 2008-06-20
i'd more guess on your mirror servers being slow. Since both, mozilla and apt use the same basic setup for network reachability it would not make any sense for one to be slowing than the other. Unless the other side is slower... and that is what i would suspect.

i'd try using a different mirror... if that is practical for you. Unfortunately i don't have a howto at hand how to change your repositories... 

hope it helps (a little) :)

---

### Post by sapient2003 on 2008-06-20
Click on System-->Administration and choose Software Sources. In the Ubuntu Software tab, change "Download from" to Other. Now click on the "Select Best Server" button.

---

### Post by ettercap on 2008-06-29
thnx every 1 got it.....

---

### Post by lisati on 2008-06-29
> **sapient2003 said:**
> Click on System-->Administration and choose Software Sources. In the Ubuntu Software tab, change "Download from" to Other. Now click on the "Select Best Server" button.
BTW, the closest server (geographically) isn't necessarily the fastest. I *sometimes* get a better speed connecting "across the ditch" to Australia.

---

