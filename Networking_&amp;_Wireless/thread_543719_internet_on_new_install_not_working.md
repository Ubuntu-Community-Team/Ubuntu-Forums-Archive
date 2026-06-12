---
title: "internet on new install not working"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by zagloba on 2007-09-05
ok Im using dsl modem connectet with cable not usb i did chec in the 
system>admin>networking and it shows my ip but no internet
on same computer i have xp and internet works fine also i have wireless on that moden turn on for my wife laptop is ther some kind of a conflict?
plz help a running unbuntu 6.10

---

### Post by guardsman85 on 2007-09-05
Please post the output of ifconfig.

---

### Post by zagloba on 2007-09-05
ok it looks like this
eth0     link encap:ethernet hwaddr 00:10:b5:f4:3f:44
            inet addr 192.168.0.2 bcast 192.168.0.255 mask 255.255.0
            inet6 addr fe80::218:b5ff:fef4:3f44/64 scope link
            up broadcast running multicast mtu:1500 metric:1
            rx packets:11 errors:0 dropped:0 overruns:0 frame:0
            tx pockets:17 errors:0dropped:0 overrun:0 carrier:0
            collisions:0 txqueuelen:1000
            rx bytes:1674 tx byts:1620
            interupt:5 base address:0x2000


lo         link encap:local loopback
           inet addr:127.0.0.1 mask:255.0.0.0
          inet6 addr: ::1/128 scop host
         up loopback running mtu:16436 metric:1
        rx packets:2 errors:0 dropped:0overuns:0 frame:0
       tx same as rx
       colission:0 txquequelun:0
       rx byts:100 tx byts:100  

hope this will help u and me :popcorn:

---

### Post by zagloba on 2007-09-06
come on some one help me 
:(

---

### Post by zagloba on 2007-09-06
help somebody 
:confused:

---

### Post by Steve1961 on 2007-09-06
Can you ping an address.  try:

ping -c 3 208.67.222.222

---

### Post by kevdog on 2007-09-06
Can you post 
lshw -C network

Its a wired connection that is not working correct?

---

### Post by guardsman85 on 2007-09-06
> **zagloba said:**
> come on some one help me 
:(
Sorry, wasn't trying to blow you off...unfortunately work and school calls some times...:)

---

### Post by zagloba on 2007-09-07
well still no internet i will be installing knoppix soon and see
if i get more luck with that one :)
thx to all 
and i be back

---

