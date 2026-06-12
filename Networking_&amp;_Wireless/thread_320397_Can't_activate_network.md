---
title: "Can't activate network"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by adamJ5 on 2006-12-17
To start off, I am a novice when it comes to computers.

So, a couple of days ago I was downloading using KTorrent and having terrible speeds (about 5 kbps). 
So I tried forwarding some ports using Firestarter, but no improvement what so ever occured.
 So I uninstalled it - wrong move. Now all my ports were blocked and I couldn't connect to the internet so I could download it. In pure hope I tried to configure my networkconnections, but with fatal results.

Now, after 3 days of trying to get it working, searchin trough every god forsaken thread here you are my only hope! :confused: 
The worst part is that I don't know what wrong! I can activate "eth0" but not "ath0". When I click "activate ath0" it just loads for about a minute and then leaves it unactivated.
 I got the windows drivers installed for my wifi-card (Atheros AR5212 chipset).
I'm complettely lost! :-k 

dhclient eth0 gives me:
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

could not execute /etc/dhcp3/dhclient-script: No such file or directory
Listening on LPF/eth0/00:08:02:40:0c:56
Sending on   LPF/eth0/00:08:02:40:0c:56
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
could not execute /etc/dhcp3/dhclient-script: No such file or directory
```

dhclient ath0:
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

could not execute /etc/dhcp3/dhclient-script: No such file or directory
Listening on LPF/ath0/00:11:95:91:99:12
Sending on   LPF/ath0/00:11:95:91:99:12
Sending on   Socket/fallback
receive_packet failed on ath0: Network is down
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
send_packet: Network is down
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
could not execute /etc/dhcp3/dhclient-script: No such file or directory
```


ndiswrapper -l:```

Installed ndis drivers:
net5211         driver present, hardware present
```


I really hope that I'll get this solved, cause there's no way that I'm going back to Windows again. :mrgreen: 

Cheers

---

### Post by adamJ5 on 2006-12-18
Anyone? I'm really needing your help :(

---

### Post by j3cakes on 2006-12-18
ok, since everyone else seems to be busy, I'll see if I can help. I'm relatively new to Ubuntu as well but I've had a couple of issues with my networking so maybe we can work it out.

Firstly, let me just see if I understand your setup - you have two network cards, an ethernet and a wireless and neither works. Is that correct?

If you go to System -> Networking, is your wireless card there? Is it enabled? What about the ethernet card?

What's in your /etc/network/interfaces file? I should say here, just in case, please don't post any public IP addresses - a public address is anything that _doesn't_ start with: 10; 172.16 to 172.31; or 192.168. (aka RFC1918 addresses))

I'm guessing you have another machine you can use to access the internet. does it use DHCP? from the same source? 

If you go to a terminal and type 'sudo ifdown eth0' and then 'sudo ifup eth0' what's the result?


> So I uninstalled it - wrong move.

are you talking about KTorrent or Firestarter? I'm guessing KTorrent but I just want to make sure. In firestarter, please make sure that you disable any outbound 'allow' policy; however, this is for testing purposes only: I'll leave it to you to determine what outbound security you require.

> I got the windows drivers installed for my wifi-card (Atheros AR5212 chipset).

(I have to ask this) Did you install the Windows drivers for your Atheros card onto your Ubuntu box? (edit: I'm not even sure this is possible :))

---

### Post by adamJ5 on 2006-12-18
> **j3cakes said:**
> 

are you talking about KTorrent or Firestarter? I'm guessing KTorrent but I just want to make sure. In firestarter, please make sure that you disable any outbound 'allow' policy; however, this is for testing purposes only: I'll leave it to you to determine what outbound security you require.



(I have to ask this) Did you install the Windows drivers for your Atheros card onto your Ubuntu box? (edit: I'm not even sure this is possible :))

First if all, thanks for your reply. 

I was talking about Firestarter. ](*,) That's the sad part.:-# 

Yeah, I did and it *does *work using [ndiswrapper](http://ndiswrapper.sourceforge.net/)

I got to get some sleep at the moment, but I'll try it tomorrow. Hope it works! :)

---

### Post by scrooge_74 on 2006-12-18
From what I read it seems your net cards are not picking the ip offering from your router, hat type of network config you have. 

Is your router or provider given the IPs automatic or it has static ip addresses?

this is important to be able to have an idea of your config.  It seems both of your cards are working

---

### Post by j3cakes on 2006-12-19
can you please post the output from 'ifconfig -a' (it might have to be 'sudo ifconfig -a', I can't remember and I'm at work right now so I can't check)

also, one option might be to assign a static IP address and DNS and see if we can get connectivity that way. go to System -> Administration -> Networking and assign a static IP address that's not in use. Remember, you also need to assign a DNS server address, usually the LAN IP for your router.

you'll probably want to get firestarter back on pretty quick. as I understand it, firestarter is just a pretty face on the firewall program that runs in the background so there are probably commands you can type into a terminal that will achieve the same thing as in the GUI, but I don't know what they are. 

so:
post the ifconfig output
assign static IP and DNS
try to ping [www.google.com](www.google.com) or do an nslookup
try ifdown/ifup and post the results.


good luck...



edit: by the way, I found [_this link_]("http://www.atheros.com/news/linux.html") which might be preferable to using the windows drivers....

---

### Post by Doug11 on 2006-12-19
I had that problem , so I installed the program I used in xp (utorrent), loaded it in wine and it works great.

---

### Post by adamJ5 on 2006-12-19
Couldn't get contact with static IP's either.


ifconfig output:

```
ath0      Link encap:Ethernet  HWaddr 00:11:95:91:99:12
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Memory:e0b40000-e0b50000

eth0      Link encap:Ethernet  HWaddr 00:08:02:40:0C:56
          inet addr:195.67.199.34  Bcast:195.67.199.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:24586 (24.0 KiB)  TX bytes:24586 (24.0 KiB)
```


I'll get back to you with ifdown and ifup

[edi] PS. It shows that I got 0% signal from the router that's standing 10 feet away from me.

---

### Post by scrooge_74 on 2006-12-19
your eth0 is been assign an IP, your wireless is not picking any network.

For your wireless you can also use the command iwconfig ath0

if you are connect to a wired network by doing "sudo ifdown eth0" and then sudo ifup eth0 you should release and get ip address from your provider and be able to get online

Post the results

Also did you installed Firestarter again, you may have close your system to the outside, I would reinstall firestarter and see what is says when you try to browse the internet.  I had my share of problems with firestarter until i got the handle of it.  You can use the wizard it includes to help you configure your ethernet card.

good luck

---

### Post by adamJ5 on 2006-12-19
SOLVED! Thanks everyone!

All I had to do was to inactivate eth0, and configure ath0 with an IP that was supported by the router.

---

