---
title: "Ethernet only shows ipv6, not ipv4 - Gutsy, Dell Inspiron 1525"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by MarkusRTK on 2008-04-09
Hi -- got a brand new Dell Inspiron 1525, the kind that comes preloaded with Ubuntu. Everything is awesome except the wired Ethernet interface, which can't get an IP from my network. I *think* it's because, for whatever reason, the interface is trying DHCP exclusively in ipv6, not ipv4. (My network can only handle ipv4; learned that the hard way with my old computer.) Wireless connects in ipv4, works fine, it's just the ethernet.

I have this theory because, in network-tools, the interface only shows IP information for ipv6, nothing for ipv4. After a while, avahi kicks in, creating another interface called eth0:avahi which claims to have an ipv4 connection, though it can't transmit data and DHCP still doesn't work. (Am I right in thinking that avahi is buggy and problematic? I remember it giving me trouble on my old comp as well. But I can't uninstall it without removing ubuntu-desktop...)

For the record, I uninstalled network-manager once this problem became apparent, no change. (I prefer doing it all from the command line anyway.)

ifconfig reads:

```
eth0      Link encap:Ethernet  HWaddr 00:1D:09:47:3A:73  
          inet6 addr: fe80::21d:9ff:fe47:3a73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:17093 (16.6 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1C:BF:B4:AC:D0  
          inet addr:140.247.157.125  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::21c:bfff:feb4:acd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56704 errors:6 dropped:3644 overruns:0 frame:0
          TX packets:4338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9921845 (9.4 MB)  TX bytes:581592 (567.9 KB)
          Interrupt:17 Base address:0x6000 Memory:fe7ff000-fe7fffff 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:09:47:3A:73  
          inet addr:169.254.4.44  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:670 (670.0 b)  TX bytes:670 (670.0 b)
```

Any suggestions? Or is this normal and I'm missing something?

---

### Post by MarkusRTK on 2008-04-12
More information:

The controller is a "Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)", according to lspci.

Uninstalled avahi; no change. Tried removing all ipv6 capabilities, a couple different ways; no change. (The ipv6 functionality would disappear from both ethernet and wireless, but still no ipv4 appeared for the ethernet.) Got desperate and reinstalled network-manager, played with it, nothing helped. I don't think it's a problem with DHCP b/c it works for the wireless; it's just that my ethernet appears only to be trying ipv6.

Could there be a problem with drivers for the card? I'm on one of those Dell Inspiron 1525s that came preloaded with Ubuntu, so you wouldn't think there'd be a problem, but you never know...

Any help would be greatly appreciated. It's important I get the ethernet working, because the wireless (which I'm using now) kind of sucks... Thanks in advance

---

### Post by Iowan on 2008-04-12
> **MarkusRTK said:**
> Hi -- got a brand new Dell Inspiron 1525, the kind that comes preloaded with Ubuntu. I'm jealous...
> Am I right in thinking that avahi is buggy and problematic? I'm not really familiar with what it's SUPPOSED to do - to me, it means something else isn't working.
What is your DHCP server?
IIRC, NM only wants to enable one interface at a time - but manually configuring **/etc/network/interfaces** should override.

---

### Post by MarkusRTK on 2008-04-12
> What is your DHCP server?

If i understand what you're asking, it's client.fas.harvard.edu. Or do you mean something else?

(I believe what Avahi does is, it jumps in to assign you an artificial IP address when you can't get one normally. Not sure why, or how that would ever work. but yeah, seems like a symptom rather than a cause.)

---

### Post by Iowan on 2008-04-14
That's what I was awkwardly trying to ask - I didn't know if the PC was direct connect to ISP,  if there was a router in between, or if a modem was providing local address.

Might "comment out" the "auto" line for **eth1** in aforementioned **/etc/network/interfaces** file, and restart networking to see if **eth0** gets an address.  Probably won't make a difference, but I wonder if **eth1** already having an address is making the system ignore your request.

---

### Post by johnnyleetsauce on 2008-04-14
I was having this problem too in my dorm but I upgraded to ubuntu 8.04 beta and it worked fine. Trust me, go to 8.04 and it works fine. Then right click your sound icon, click preferences and then change to the OSS thing and turn up your volume a little. Thats all I did to get sound and internets working.

---

### Post by MarkusRTK on 2008-04-15
Fixed it! Thanks guys but it turned out to be a driver problem. The preconfigured driver for this card, sky2, apparently is not very good -- I saw it described on another board as a ["pile of steaming dung"](http://www.linuxquestions.org/questions/slackware-14/any-solution-for-the-sky2-driver-for-marvell-8056-549244/) -- so instead I downloaded an old driver, [sk98lin](http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=10013&term=typ.treiber+bs.Linux+produkt.SK-9E21D&produkt=produkt.SK-9E21D&typ=typ.treiber&system=bs.Linux), and bingo! it worked perfectly.

(Getting sk98lin to work was something of a procedure, though. If anyone else needs to do this and is curious: first i had to change the hashbang on the script sk98lin came with from sh to bash in order for it to execute, which seems like a weird oversight. Then I had to make a symlink to mykernel headers. Then it didn't remove the old sky2 driver like it claimed it did, and loading them both naturally just messed everything up, plus blacklisting sky2 didn't work for some reason, so i had to go delete the old sky2.ko file directly. But now it works!)

Appreciate everyone's help with this. I am enjoying my ethernet right now!

---

