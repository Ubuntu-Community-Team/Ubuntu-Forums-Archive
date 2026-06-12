---
title: "eth0 disappeared..."
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by alphabets on 2006-12-19
So today I finally moved my linux box into my room. For a while it was sitting next to my wireless router doing nothing. I finally figured out how to use my ethernet port on my Mac as an outbound so that I can share the internet connection with another computer. After moving my monitor and my box over to my room and get it all hooked up I boot it up. I tested out the internet connection and it was a no go. I go into Network Settings and the only connection in there is ppp0... 

This is where the troubleshooting begins...
- I tried putting the network card in a different PCI slot, with no difference what so ever.

- If you look [HERE](http://ubuntuforums.org/showthread.php?t=315060) there is someone with a similar problem, except my network card doesn't even work in the liveCD.

- ifconfig -a reads:
[PHP]
lo                Link encap:Local Loopback
                   inet addr:127.0.0.1 Mask:255.0.0.0
                   inet6 addr: ::1/128 Scope:Host
                   UP LOOPBACK RUNNING MTU:16436
                   RX packets:73 errors:0 dropped:0 overruns:0 frame:0
                   TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
                   collisions:0 txqueuelen:0
                   RX bytes:5304 (5.1KiB) TX bytes:5304(5.1kiB)

sit0              Link encap:IPv6-in-IPv4
                   blah blah, blah blah
(noting beyond this point)
[/PHP] 

- lshw -C network reads:
[PHP]
*-network UNCLAIMED
description: Ethernet controller
product: Realtek Semiconductor Co., Ltd.
vender: Realtek Semiconductor Co., Ltd.
physical id: c
bus info: pci@02:0c.0
version: 00
width: 32 bits
clock: 33MHz
resources: ioport:df40-df5f irq:5
[/PHP]

PLEASE NOTE:: The card worked GREAT up until I moved it from sitting next to my router. No, I did not drop it along the way. ;)


Thanks in advanced to ANYONE that helps me with this!!

-Kyle/Alphabets

---

### Post by alphabets on 2006-12-20
Bump... ](*,)

ALSO NOTE:: The realtek device IS my network card!

---

### Post by alphabets on 2006-12-22
Bump... :(

---

### Post by mistypotato on 2007-01-06
I'm running into this same exact problem now so I'm wishing you had gotten help ;)

---

### Post by Mba7eth on 2007-01-06
i'm not that experienced but maybe ur interface have been shut 
first of all reboot ur system 
then type ifconfig see if it is seen by ur kernal as an interface 
if no good results try this 
#sudo ifup eth0

otherwise you must get an answer from  a more experience people

Cheers 

Mba7eth:mrgreen:

---

