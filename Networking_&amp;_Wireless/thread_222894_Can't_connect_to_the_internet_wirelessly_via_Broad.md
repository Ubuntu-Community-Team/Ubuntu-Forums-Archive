---
title: "Can't connect to the internet wirelessly via Broadcom BCM4306"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by Epperly on 2006-07-25
I can't connect my HP ze5700(ze5738rs) to the internet via wireless, I tried to follow some guides but I can't apt-get because it also, luckily:rolleyes:, won't connect to the internet wired when I try to.

No wireless, no wired... how the heck am I supposed to get on the internet with this thing(besides sticking to windows)?

Please help!
Thanks!

---

### Post by Ben Armston on 2006-07-25
This sounds as though it might be a routing problem. Could you connect up the wired network and then post the output of 

```
/sbin/ifconfig
/sbin/route
```

---

### Post by BetaMaster on 2006-07-25
I have the same chipset Broadcom as you, and I can't get internet to work either. Is it showing up as eth1 for you too?

---

### Post by Epperly on 2006-07-25
(I got it wierd, I realized I was missing the DNS server.)

Ben:
```

patty@LAPTOP:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:20:26:AA:B8
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fe26:aab8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:53041166 (50.5 MiB)  TX bytes:2182707 (2.0 MiB)
          Interrupt:10 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

patty@LAPTOP:~$ /sbin/route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
patty@LAPTOP:~$

```

eth0 is my main wired network

Beta: Yes, the wireless shows up as eth1

---

### Post by Ben Armston on 2006-07-25
> **Epperly said:**
> (I got it wierd, I realized I was missing the DNS server.)


So you can now connect to the internet via the wired network? If so, I'll leave you to apt-get whatever you were apt-getting before.

---

### Post by Max Velocity on 2006-07-25
I'm in the same situation as you guys are with the same chip (BCM4306) on a HP Pavillion Ze5416EA

Tried using a Ndiswrapper, but i didn't see any difference, still eth1

---

### Post by Epperly on 2006-07-25
Yes Im connected via wired network. And I can't apt-get bcm4306-firmware...

So, help me please. :) or.... us

---

### Post by Max Velocity on 2006-07-25
just reading up on the Ndis wrapper wireless troubleshooting guide, and it talks about the ubuntu driver blinding the windows driver.

It might be worth looking into: [https://help.ubuntu.com/community/WirelessTroubleshootingGuide](https://help.ubuntu.com/community/WirelessTroubleshootingGuide)

Edit: it's a dead link! ](*,)

---

### Post by Epperly on 2006-07-25
Didn't work for me, couldn't find packages

---

### Post by Max Velocity on 2006-07-25
Which distro you using? I'm on Xubuntu, the only problem is that I need to switch off the native linux driver, then it should just work.

the packages are bundled with ubuntu, all you need to do is look for them in your repositories, and install them from there


here's the guide:

[https://help.ubuntu.com/community/wifidocs/driver/ndiswrapper](https://help.ubuntu.com/community/wifidocs/driver/ndiswrapper)

and the driver files are in windows in the inf and system32 directories.

---

### Post by Epperly on 2006-07-25
Yea I just switched to xubuntu, too... because well, this laptop sucks haha.
You got it working?

---

### Post by punkybouy on 2006-07-25
How did you post the messsge if you can't connect?

---

### Post by Max Velocity on 2006-07-25
We've both got 2 machines ;) and we both have them on wired.

Not yet, mucking around with a few settings trying to get the static ip to work, but failing miserably.

---

### Post by Epperly on 2006-07-25
First I was on my PC which is wired, haha.
But now I'm on the laptop cause I got the wired to work, so I can download if I need to, then once I get wireless working I take the wire out put it back on the PC, tricky huh

---

### Post by Epperly on 2006-07-25
Max you got it working? I don't get the native linux driver thing, what'd I have to do?

---

### Post by Max Velocity on 2006-07-25
> **Epperly said:**
> Max you got it working? I don't get the native linux driver thing, what'd I have to do?

Not yet, just follow the instructions carefully to the link I sent you.

Which laptop you got? might just be our make :S

---

### Post by Epperly on 2006-07-25
HP ze5738rs(unfortunately ha)

---

### Post by Max Velocity on 2006-07-25
> **Epperly said:**
> HP ze5738rs(unfortunately ha)

Ah you beat me I got an older one!, still it's quite fast! I got a Hp Pavillion ze5416EA!

got the ndiswrapper to work yet?

---

### Post by bensexson on 2006-07-25
I used this guide to get connected in Dapper: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

---

### Post by Max Velocity on 2006-07-25
Soon as you get that to work, then we need to solve this problem:

> Another driver loads and binds to the device

      Sometimes ndiswrapper is used prematurely. There may be a native driver that comes with Ubuntu which is taking the primary driver position and conflicting with ndiswrapper. For more information on this, go to the WirelessTroubleshootingGuide and view the step on device drivers.

---

### Post by Max Velocity on 2006-07-25
> **bensexson said:**
> I used this guide to get connected in Dapper: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

how did you solve your problem?

---

### Post by Epperly on 2006-07-25
ungh, I got my driver installed from ndiswrapper, but it still won't connect and Idk why

---

### Post by Max Velocity on 2006-07-26
Yeah, you in the same situation as me, just need to disable the linux drivers, which is a right pain to get to work.

---

### Post by Epperly on 2006-07-26
How do I disable the linux drivers?
Tell me when you get it to work... you got any chat clients? :) hah

---

### Post by Max Velocity on 2006-07-26
Heh, but of course ;) , which IM?

---

### Post by Epperly on 2006-07-26
one of the two I have, look by my bean count

---

### Post by Max Velocity on 2006-07-27
Laptop took a turn for the worst, and lost my bootsector and Xubuntu in the process :mad: 

Grub became corrupted when I added a new partition. Do you know of any other good boot loaders?

---

