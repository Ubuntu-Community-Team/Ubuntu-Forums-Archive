---
title: "Newbie Networking, again?"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by MrClod on 2008-04-23
Hi I'm blissfully ignorant on just about everything, so I decided to connect my Ubuntu (Gutsy) to my windows 2000 with a crossover cable.  
Now, in the Ubuntu machine, I've installed an extra nic, one is connected to my dsl modem and the other connects to the win 2k via crossover cable.  I don't intend on sharing the internet connection, just to use the win 2k machine for file sharing and backup.
The two computers apparently see the conection, but can't ping eachother.  I've tinkered with Network Manager, shows eth1 & eth0.  eth1 is set for dhcp & enabled.  Fine fast internet, too.
So I've tried to enable eth0 with static ip (192.168.1.3,  255.255.255.0--the win2k is static too, set to 192.168.1.2, 255.255.255.0), and I lose my internet.  I've played with webmin, which seems to edit my etc/network/interfaces...and makes me lose internet after reboot.  I must be missing some steps, as even without internet the 2 computers still can't share & browse.  File & printer sharing is installed, just for test purposes I have "My Documents" shared on the win2k.  I believe Samba is installed as well on the Gutsy.
But...on this ubuntu machine, in places\network, I see a "Windows Network"  in there I find "workgroup"  but nothing past that.
If anybody's patient enough to walk me through what I should do, or requires more info, that'd be great.
Perhaps I should take up a more normal hobby, like collecting machetes & swords...

---

### Post by The Cog on 2008-04-23
Do an ifconfig on the Ubuntu machine and check that the relevant interface shows the word RUNNING.

P.S.
Good grief this forum is screwed up isn't it. The quick reply buttons don't work, the quote, code, bold buttons don't work. I hope they fix it soon.

---

### Post by MrClod on 2008-04-26
> **The Cog said:**
> Do an ifconfig on the Ubuntu machine and check that the relevant interface shows the word RUNNING.

P.S.
Good grief this forum is screwed up isn't it. The quick reply buttons don't work, the quote, code, bold buttons don't work. I hope they fix it soon.

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:B5:B7:0F:96  
          inet addr:192.168.1.46  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::210:b5ff:feb7:f96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1220661 (1.1 MB)  TX bytes:188200 (183.7 KB)
          Interrupt:9 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:40:33:A5:0E:6E  
          inet6 addr: fe80::240:33ff:fea5:e6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10129 (9.8 KB)  TX bytes:15611 (15.2 KB)
          Interrupt:10 Base address:0x3400 

eth1:avah Link encap:Ethernet  HWaddr 00:40:33:A5:0E:6E  
          inet addr:169.254.4.244  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x3400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Seems to be the case...

---

### Post by The Cog on 2008-04-26
That's not good. Your eth0 shows that it's up and working with an IP address 192.168.1.46 - not the address you said, but close enough.

However, your eth1 which I assume is connected to your DSL modem doesn't have an IP address at all. 

You can ignore the eth1:avah interface - it's not doing anything useful. Also ignore the lo loopback interface. They don't figure in this problem.

So your problem is that the eth1 interface to your internet isn't getting an IP address. Now, the word RUNNING is there, so we know that the cable is connected and there is something at the other end of the cable. We also see a few transmitted and received packets. I don't think it's a hardware issue. How do you normally configure the interface to the DSL modem? Do you configure it for DHCP? I hope so, since that's the easiest. IF so, try this command from the command line, and see what happens:
```
sudo dhclient eth1
```
If that works, try using the network manager to set eth1 for dhcp. 

Actually, it occurs to me that you may simply have eth1 and eth0 confused - try pulling the cable from one of them, then run ifconfig again and see which one loses the RUNNING status. If you're dead lucky, just swapping the cables might do the trick.

---

### Post by MrClod on 2008-04-30
UPDATE:  It was the cable (isn't it always?).  Replaced that & I'm pingin' like a 'mofo. 
Each computer can browse each other now, but...
It times out transferring large files, which is why I want them networked in the first place!  Something about Samba... several other lengthy threads have the same problem without any clear solution.  Thanks for you support!
:popcorn:
Pass the buttah!

---

