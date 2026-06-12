---
title: "onboard nic inop in ubuntu but ok on vista 64"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by lincoln32 on 2008-11-11
ecs 945gct-m1333 v3 e6500 intel 2.33 and new bios realteck rtl 8101E pci v01 on board      HH 8.04 no etho0 in if config but module is loaded working on usb wifi and green lan light on and yellow light flashes if wifi on but still no etho0 
I move large files so I need network speed Help lan is working on vista and on same m/b in another pc just not on this one

---

### Post by lincoln32 on 2008-11-21
It seems to be same as other posts that after vista updates card ubuntu inop
net card so after three weeks of no ubuntu I installed a d-link card and all is well other than unable to use internal gigabit card but 100 is better than 54g till a cure is found

---

### Post by lincoln32 on 2008-11-24
one day later now the new second card inop in ubuntu d-link hat ca windows be doing to network cards?

---

### Post by Bucky Ball on 2008-11-24
You should be looking for wlan0 for wireless, not eth0. Can you post the results of:

```
ifconfig
```

I am assuming you can connect through cable (eth0).

---

### Post by lincoln32 on 2008-11-26
I am trying not to use wireless as i move large files since last post I have
got the second network card to work--it was not all the way in after working on some other parts. and I built a second pc with the same board
a ecs 945gct-m1333 v.3 and when I updated I did not update the windows driver for the realteck 8108e network card and it is working on both ubuntu and windows so now I need to find drivers to revert back on windows side and see it I can make my pc work on both sides. but why should a windows driver update stop linux from working and if the driver flashes the net card
will the card ever work on ubuntu again?

---

### Post by Bucky Ball on 2008-11-27
> **lincoln32 said:**
> but why should a windows driver update stop linux from working?

It won't. The two OSs have nothing to do with each other (windoze won't even recognise the EXT3 partition Ubuntu is on without persuasion, let alone alter the setup). If you card is not working Ubuntu you have a problem with the Ubuntu setup.

---

### Post by lincoln32 on 2008-11-28
but this running on the second d-link card

todd@todd-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:50:ba:07:2c:d3  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fe07:2cd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21441 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19707375 (18.7 MB)  TX bytes:4459828 (4.2 MB)
          Interrupt:18 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96284 (94.0 KB)  TX bytes:96284 (94.0 KB)

---

