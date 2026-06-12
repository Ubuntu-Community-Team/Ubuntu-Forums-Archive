---
title: "Realtek 8139 D rev10 NIC"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by jonli447 on 2006-11-05
Hello,

I am having problems getting my realtek 8139D NIC pci card to connect to the internet.

I've read some of the posts in other threads, but have not have any success.

"sudo lsmod" shows that 8139too and 8139cp are both loaded.  I've tried blacklisting 8139too and 8139cp (one at a time of course) in /etc/modprobe.d/blacklist.  When 8139too is blacklist, Ubuntu doesn't even detect the card.  Black listing 8139cp, the card is detected, but as usual, won't connect to the internet. (I can't ping my router or any other device on my network either.  I can only ping 192.168.12.17 and localhost at 127.0.0.1).

I use static ips with as follows:
ip = 192.168.12.17
netmask = 255.255.255.0
gateway = 192.168.12.254
(dns = 192.168.12.254)

lfconfig reflects the above ip settings for eth0.

I read that there are some IRQ issues with this card.  I tried adding noapci to grub, but this did not fix anything.

The card works fine in Windows XP.  Also, Ubuntu on my labtop that has a different NIC (Intel Pro 1000/MT) can connect to the internet with no problem.  I experimented with the labtop and used the same static ip settings (just changing 192.168.12.17 to 192.168.12.16) and it worked fine.  So, I really don't think the problem is my router/network.

So, I guess I'm asking if someone knows how to get this card to work with Ubuntu, if they would please help; it would be much appreciated.

Thanks,

Jon

---

### Post by DaveBorealis on 2006-11-05
> **jonli447 said:**
> I can only ping 192.168.12.17 and localhost at 127.0.0.1).
To me it looks like the card and module do work, you just can't get out onto the network.

What do you get for these commands?
```

$ ifconfig -v
$ route -n

```

Dave

---

### Post by jonli447 on 2006-11-05
Hello Dave, here is the output of the commands.

ifconfig -v:

eth0      Link encap:Ethernet  HWaddr 00:30:BD:2B:4E:F3  
          inet addr:192.168.12.17  Bcast:192.168.12.255  Mask: 255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:804 (804.0 b)  TX bytes:804 (804.0 b)

route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.12.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.12.254  0.0.0.0         UG    0      0        0 eth0

---

### Post by DaveBorealis on 2006-11-05
> **jonli447 said:**
> 
          inet addr:192.168.12.17  Bcast:192.168.12.255  Mask: 255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1


Your card is up and running at 192.168.12.17 
> 
0.0.0.0         192.168.12.254  0.0.0.0         UG    0      0        0 eth0

And your gateway is 192.168.12.254, but you can't ping it.

And if you do 'cat /etc/network/interfaces', you get something like
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.12.17
netmask 255.255.255.0
gateway 192.168.12.254
<snip>

```

I don't believe the ethernet card would be working if there was an issue with its IRQ number...although I'm far from an expert...however by any chance do you have a second ethernet card in the machine?  It's possible that their IRQs are switching between reboots.  Or at least that used to be an issue with Linux.

---

### Post by jonli447 on 2006-11-06
Yeah, my /etc/network/interfaces is looks like the part you posted.  I do have a wlan pci card in the computer.  I could not get that card to work (even with a ndiswrapper).  I suppose I'll try removing the wlan card and seeing if it works.

---

### Post by jonli447 on 2006-11-06
Nope, pulling out the card didn't work.  I also tried reinstalling Ubuntu; diabling 8139cp in /etc/modprobe.d/blacklist .  I'm at a lost on how to fix this.  Is this chipset no longer supported by kernel 2.6?

---

