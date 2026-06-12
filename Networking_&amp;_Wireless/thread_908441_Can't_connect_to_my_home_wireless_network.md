---
title: "Can't connect to my home wireless network"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by JungleBeast on 2008-09-02
Hello there, I've set up a wireless network in my home.
O2 wireless II box by Thompson

The network is up and running and I have no problem connecting in windows on wireless, under WEP encryption, or no encryption.

In ubuntu 7.10 32bit I can detect the network "O2wirelessBBBA1D" 
and whether in WEP where i type in the 64 bit hex key or in unencrypted. It goes away and the 2 balls circle (on the nm-applet in the top left hand corner) each other endlessly. permanently waiting for feedback from the wireless box. 

Anyone know what I'm doing wrong? or what could be the cause?
any hints would be good!! 


Also i've tried it through the terminal using:
```
sudo iwconfig wlan0 essid O2wirelessBBBA1D key xxxxCxxxxE
sudo dhclient wlan0
```

where xxxxCxxxE closely resembles my key with x's as digits.

using this i can detect the network is there and details about it, but still can't connect.


Thanks for any help!

---

### Post by felker2 on 2008-09-02
Are you using Ubuntu 7.10? If so, I have *no* answer for you.

However, in Ubuntu *8.04* with kernel 2.6.24, there's a bug (with centrino / intel wifi): it can't connect to WEP encrypted APs.

See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223111](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223111)

Workaround for 8.04: install linux-backport

---

### Post by JungleBeast on 2008-09-04
Thanks felker, that could have been exactly the solution for me.

unfortunately i'm definitely 7.10  although i have received all the updates, but i don't think that would have introduced any bugs?

Also i'm using amd64 (but running 32 bit ubuntu - as the 64 gave me far too many headaches) and a d-link wireless card.

Any other ideas? anyone?

also has anyone else got the o2wireless running on ubuntu? 

thanks

---

### Post by Nylo on 2008-09-04
> **JungleBeast said:**
> Thanks felker, that could have been exactly the solution for me.

unfortunately i'm definitely 7.10  although i have received all the updates, but i don't think that would have introduced any bugs?

Also i'm using amd64 (but running 32 bit ubuntu - as the 64 gave me far too many headaches) and a d-link wireless card.

Any other ideas? anyone?

also has anyone else got the o2wireless running on ubuntu? 

thanks

I did have it working....  That is until I received a Ubuntu update.  Now my WiFi connect is gone and no matter what I do I cannot get it back.

Ubuntu's network manager has got to be one of the buggiest programs that I have come across in a long time.  It has a mind of its own!  

I'm going to try and manual configure my WiFi.  If I don't come back tell my family I love them!  :biggrin:

---

### Post by felker2 on 2008-09-04
I think the problem is in kernel 2.6.24. I don't whether Ubuntu 7.10 upgrades to that kernel. Check with "uname -a".

---

### Post by JungleBeast on 2008-09-06
Thanks felker, well the problem has got more interesting/strange, but first i'll give you the outputs.

For uname -a I get:
```
chris@spiral:~$ uname -a
Linux spiral 2.6.22-15-generic #1 SMP Wed Aug 20 18:39:13 UTC 2008 i686 GNU/Linux
chris@spiral:~$ 
```

I've also got outputs for ifconfig:
```
chris@spiral:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:89:9E:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13796 (13.4 KB)  TX bytes:13796 (13.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:6E:61:40  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe6e:6140/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6195 (6.0 KB)  TX bytes:5600 (5.4 KB)
          Interrupt:20 

chris@spiral:~$ 

```

and also for trying to log on through the terminal: 

```
chris@spiral:~$ 
chris@spiral:~$ sudo iwconfig wlan0 essid O2wirelessBBBA1D key ##########
[sudo] password for chris:
chris@spiral:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:95:6e:61:40
Sending on   LPF/wlan0/00:11:95:6e:61:40
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.254
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.65 -- renewal in 42515 seconds.
chris@spiral:~$ 
```

just in case any of that means anything to you.

Also I'm currently on manual network configuration. as i wasn't getting any joy with roaming either.


Here's the strange bit: aving done all the above in the terminal, i checked firefox, just on some wild hope. And i got 5 seconds of internet!!  just long enough for the RSS feeds to load, but no more.  Strange eh??
But no more internet. (And of course it's nothing to do with the network as here i am happily typing away on wireless on the windows dual boot.)

Any ideas? And 2.6.22-15-generic, did that have the bug?

thanks again,

chris

---

