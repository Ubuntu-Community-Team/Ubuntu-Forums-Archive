---
title: "no wireless connection, help please!!!!!!"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by elquer on 2007-06-03
i just installed a fresh copy of ubuntu 7.04 on my compaq pressarion v2000 laptop with amd 64 turion processor and ati radeon xpress 200m graphics card. i'm having two issues so far that i can't seem to get around. i can't figure out how to get the wireless card working on feisty fawn, even though i got it to work on 6.06. can someone give me detailed info on how to get that to work, i'm not linux savy, so any tech words will put me off course, and also, i know about the flash player and 64 bit contradiction, i was able to get opera to work fine with flash 9 but again, can't figure it out on 7.04. please help me with that as well. thanks for the help guys.

---

### Post by uman2008 on 2007-06-03
You forgot to mention what wireless card are we talking about, but lets suppose its broadcom, if thats the case, then you can get it to work with either ndiswrapper or bcm43xx module. So, try and search forum with this two keywords, ndiswrapper and bcm43xx.

---

### Post by kevdog on 2007-06-03
Please post chipset of card, and what methods you attempted to get wireless card to work -- ndiswrapper or bcm43xx.

This would help a lot.

---

### Post by elquer on 2007-06-03
the card is a brodcom bcm4318, i've tried the ndsiwrapper and i dont' know if i made any mistakes but it didn't work, i remember using a howto for my 6.06 and it worked perfectly fine, but i didnt' bookmark. thanks for the replys

---

### Post by kevdog on 2007-06-03
Can you post the line from:

```

lspci | grep Network

```

Thanks

Also are you requiring any encryption with your connection -- specifically WPA??

---

### Post by elquer on 2007-06-03
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


my home wireless network is encrypted with wep 128 key, my aim is elquer2004 if ur online and willing to help i'll be glad to receive ur assistance, thanks for the quick reply.

---

### Post by kevdog on 2007-06-04
I would use AIM if I had it installed.

I dont know any other way, but you are probably going to have to reinstall ndiswrapper along with your specific driver for your card.

This sounds like a bitch -- and it is. 

Before abandoning all hope -- and Im sure youve done this -- turn off any WEP or Mac filtering on your router and see if you can connect.

If you cant (which is probably the case) do you have any other computer that can connect to the internet???
If you know how -- do you know if ndiswrapper is installed on your system???

Can you post the following (just want to make sure your card is compatible with ndiswrapper).
lspci -n | grep 05:02.0

can you also post the following
ifconfig
/etc/network/interfaces file.

Sorry about the laundry list

---

### Post by elquer on 2007-06-04
elquer@elquer-laptop:~$ lspci -n | grep 05:02.0
05:02.0 0280: 14e4:4318 (rev 02)
elquer@elquer-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:33:65:91  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe33:6591/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15608 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16383625 (15.6 MiB)  TX bytes:2176442 (2.0 MiB)
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

elquer@elquer-laptop:~$ /etc/network/interfaces file.
bash: /etc/network/interfaces: Permission denied
elquer@elquer-laptop:~$ 

those are the results of ur instructions up there, and, i had my laptop online when i had 6.06 and it was working perfectly fine, but i upgraded to 7.04 and i'm not understanding it too well.

---

### Post by MeeMaw on 2007-06-04
> **elquer said:**
> 
elquer@elquer-laptop:~$ /etc/network/interfaces file.
bash: /etc/network/interfaces: Permission denied
elquer@elquer-laptop:~$ 

those are the results of ur instructions up there, and, i had my laptop online when i had 6.06 and it was working perfectly fine, but i upgraded to 7.04 and i'm not understanding it too well.

Try     "cat  /etc/network/interfaces"      to look at that file, then post it here.    ;)

---

### Post by elquer on 2007-06-05
elquer@elquer-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

elquer@elquer-laptop:~$

---

### Post by MeeMaw on 2007-06-06
Try this post;

[http://ubuntuforums.org/showthread.php?t=424994&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=424994&highlight=bcm4318)

Good luck!!!!

---

