---
title: "network problem similar to others - still unsolved"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by klep on 2006-08-04
Hello, 


I read a thread about this same problem earlier but I can not find it anymore. Sorry about that.


I was using the previous version of ubuntu (sorry im not sure of the name... breezy maybe?) and everything was fine but I kind of stopped using it and gradually used XP more and more again.

I deleted that partition and started again with the latest version using a CD from snedit just today.

From the live cd the internet worked. In my previous install of the old version the internet worked. Now I have installed the new version the internet does not work (i repeat though that it did work in the liveCD).


When i go in to the network properties and select to use a static IP address and enter some crap details (111.111.111.111 etc) and then go back in and make it dynamic the internet suddenly starts working.


This is the exact same behavour I read in another thread. That thread did not have a solution. 

I am using a gigabit ethernet card built on to my abit motherboard.


Does anyone have any suggestions as to what I should do? 

Cheers,

---

### Post by kb3hkg on 2006-08-04
can you post what ifconfig says about the interface by default please

---

### Post by stormblue on 2006-08-05
> **klep said:**
> 

When i go in to the network properties and select to use a static IP address and enter some crap details (111.111.111.111 etc) and then go back in and make it dynamic the internet suddenly starts working.



You can't enter "crap details" and expect it to work.  For example, your IP address probably has to be 192.168.0.x or 192.168.1.x.  

Are you having issues with the dynamic internet?

---

### Post by klep on 2006-08-05
Sorry, i should have made it clearer. The reason i enter nonsense is not that I expect that to work, but because I read that when you change the eth0 connection to use a static ip address (details of that address do not matter) and then change it back to use DHCP the internet suddenly starts working.
Sure enough this is exactly what happens.


I shall now post details of ifconfig by default. Just let me start the pc.

cheers

---

### Post by klep on 2006-08-05
By fefault the ifconfig says:

eth0      Link encap:Ethernet  HWaddr 00:50:8D:D5:C1:85
          inet6 addr: fe80::250:8dff:fed5:c185/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:180 (180.0 b)  TX bytes:468 (468.0 b)
          Interrupt:217 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)



note that I noticed a difference in the inetaddr line of the above when comparing the default ifconfig when the pc first loads and when ive done the DHCP trick. After doing the dhcp trick it lists some ip addresses. I went in to network properties and said to use a static ip. Have given myself an ip, using a mask of 255.255.255.0 and the gateway being my routers IP and this is working fine.


My question is, is this an appropriate solution? I dont see why it wouldnt be but then i'm a networking noob and could be ignoring a big problem.


Thanks.

---

