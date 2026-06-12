---
title: "Updates took away my wireless connection?"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by Mimsy on 2007-02-11
Help, please?

Since I installed the latest updates, network-manager-gnome cannot see my wireless device anymore. (That would be the W200 I refer to in my signature below. It's still on the N410c laptop, built into the lid.) In the Network Manager that came with Dapper, I can see the eth1 connection, the card is marked as "activated", and I can go in and reenter my settings, WEP security, and the hexadecimal passphrase. I can even save them, but I can't connect. 

I have tried to uninstall network-manager-gnome with "aptitude remove", and then reinstall it again, but no change. How can I make Network Manager realise that I am on a laptop, and that it needs too be wireless?

In case it is helpful, here is the output from ifconfig:
> 
mimsy@mimsy-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:59:C6:88:F7
          inet addr:192.168.63.102  Bcast:192.168.63.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fec6:88f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47201 errors:2 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:77468234 (73.8 MiB)  TX bytes:5287713 (5.0 MiB)

eth1      Link encap:Ethernet  HWaddr 00:08:02:44:6C:80
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:312 (312.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1072 (1.0 KiB)  TX bytes:1072 (1.0 KiB

The wireless W200 is eth1. Eth0 is right now set as default device, and it is working just fine, as long as I keep one end of hte cable connected to the laptop, and the other to the wireless router/hub. The windows laptop iw able to connect t the router, as is the desktop PC and the Xbox 360, so logically, the problem is all in my laptop. Laso, I would rather not change the router settings around too much, since I need to reconfigure the other three devices every time I do. If there is no other way, I will not complain about having to do it, but I would prefer to try other methods first, if there are other methods.

All help appreciated,
Mimsy

---

### Post by Mimsy on 2007-02-13
No one?

---

### Post by chordmasta on 2007-02-13
I am having the same issue. Installed fresh yesterday, detected my broadcom wireless. Did an update, now its gone. Any solution?

---

### Post by Mimsy on 2007-02-13
I am making some progress, though not much. After removing all of network-manager-gnome (NMG), using the "aptitude purge" command, I removed the notification area from my panel. I then reinstalled NMG and the notification area to the panel again - NMG appeared, clearly visible, and with both wired and wirelss networks showing. I entered all information about my network, but to my annoyance, I still can't connect. I can see the network in the list of available wireless networks, but I cannot connect to it.

At least things are moving in the right direction. Suggestions? :)

/Mimsy

---

### Post by Mimsy on 2007-02-14
No luck yet. I can't even see my network in the list of available networks anymore, and I can't connect even even when I drop security on the router to nothing. Completely open and unsecured, and I still can't connect.

I've been working at this for over a month now... help me, before I kill something. Please.

](*,) 

/Mimsy

---

