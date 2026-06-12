---
title: "No networking whatsoever on this computer"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by blastus on 2008-04-14
I don't understand what is wrong with this one computer. It is about 5 years old and I have never, not once, had an issue with wired networking until now. The Windows XP and Ubuntu 7.10 recognize the network card but neither can connect to my router anymore on this machine...

1. I know the network cable works because it works on a different computer
2. I know my router and modem work; I have two other computers and have no problems connecting to my router with them
3. I have tried two different network cards (RealTek and StarTech) in two different PCI slots ;these are network cards I have used for several years in this computer and others with absolutely no issues in Windows XP and Ubuntu
4. I have verified that the 100 Mbps light is on on the network card and the Ethernet connection light is on on my router when hooked up to this computer
5. I have tried powering everything down (physically unplugging all cables and power cords) for up to 5 minutes, and plugging everything back in again
6. I have messed around in the BIOS (clearing NVRAM data, RealTek BIOS boot settings), changed router settings (domain name, IP address pool), etc...
7. Tried Windows XP, Ubuntu 7.10 as installed, and the Ubuntu 7.10 Live CD

It's like this computer has become completely useless for networking--absolutely no networking works. Does anyone have any recommendations?

Edit: This computer does not have an onboard LAN.

---

### Post by greenstar on 2008-04-14
Post the output of:
```
ifconfig -a
```

Greenstar

---

### Post by blastus on 2008-04-14
> **greenstar said:**
> Post the output of:
```
ifconfig -a
```

Greenstar

```
eth2      Link encap:Ethernet  HWaddr 00:00:B4:91:DD:16  
          inet6 addr: fe80::200:b4ff:fe91:dd16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:6939 (6.7 KB)
          Interrupt:17 Base address:0xe700 

eth2:avah Link encap:Ethernet  HWaddr 00:00:B4:91:DD:16  
          inet addr:169.254.6.254  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe700 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2473 (2.4 KB)  TX bytes:2473 (2.4 KB)
```

At one point I had two network cards in this computer a few months ago when I was using it as a gateway.

---

### Post by greenstar on 2008-04-14
Let's force the interface to release and renew.
```
sudo ifdown eth2
sudo ifup eth2

```
Post the output of the last one.

Greenstar

---

### Post by blastus on 2008-04-15
```
There is already a pid file /var/run/dhclient.eth2.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth2/00:00:b4:91:dd:16
Sending on   LPF/eth2/00:00:b4:91:dd:16
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Stopping the Firestarter firewall...
eth0: error fetching interface information: Device not found
eth0: error fetching interface information: Device not found
eth0: error fetching interface information: Device not found
   ...done.
 * Starting the Firestarter firewall...
eth0: error fetching interface information: Device not found
eth0: error fetching interface information: Device not found
eth0: error fetching interface information: Device not found
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 2
```

---

### Post by greenstar on 2008-04-15
Post the output of:
```
cat /var/run/dhclient.eth2.pid
```

---

### Post by blastus on 2008-04-15
```
cat /var/run/dhclient.eth2.pid
```

Output: ```
6686
```

What do you think it might be?

---

### Post by greenstar on 2008-04-15
OK, let's backup this file and remove the original:
```
sudo mv /var/run/dhclient.eth2.pid /var/run/dhclient.eth2.pid.original
```Now let's reboot and see if Ubuntu 'sees' your ethernet card. It should automatically install it if it's found, probably as eth0. Then, presuming it's discovered, we'll configure it if necessary. 

If all else fails, we can go back to the present configuration by doing:
```
sudo mv /var/run/dhclient.eth2.pid.original /var/run/dhclient.eth2.pid
```HTH,

Greenstar

---

### Post by blastus on 2008-04-15
I did the move and rebooted. The device still shows up as eth2 and the output of ifconfig -a looks the same as before. It can't connect to my router. The thing is is that this doesn't work in Windows XP or with the Ubuntu 7.10 LiveCD either.

Tomorrow I'll try hooking this computer up to another computer and see if I can ping it. If that works then I'll reset my router--I think it clears out everything on it which is different than just unplugging it and plugging it back in again. I was thinking that maybe the router has blacklisted the MAC addresses (if that's possible maybe it thinks the MAC is spoofed I don't know) of the network cards I tried or something...maybe the host name has to be unique on the network (I've tried changing the host name on the computer as it was the same as a wireless computer on my network, but that didn't fix the issue.) 

Thanks a lot for all your help!

---

### Post by Cristinalee on 2008-04-15
There is often problems with my computer .So i hope you can help me solve the problems.

---

### Post by blastus on 2008-04-15
Man do I feel like a dummy.:lolflag:

I checked my router settings again and remembered that I had enabled MAC address filtering. Of course the one network card that was on that list is in my new computer now and it's in there because I couldn't get the built-in network card to work...and of course it doesn't work because the MAC address of the card isn't in my router!!

This has been a long series of tragic coincidences involving several computers and shuffling several network cards. I mean, if I track back the network cards I've moved around, I've moved them around in such a way that the computer I had issues with didn't have a network card in it whose MAC address was registered with my router. I WILL NEVER USE MAC ADDRESS FILTERING EVER AGAIN. It provides no security either and is a huge pain in the butt.

Everything is working now.

> **Cristinalee said:**
> There is often problems with my computer .So i hope you can help me solve the problems.

Sure I can try. What's the issue?

---

### Post by greenstar on 2008-04-15
> **blastus said:**
> I did the move and rebooted. The device still shows up as eth2 and the output of ifconfig -a looks the same as before. It can't connect to my router. The thing is is that this doesn't work in Windows XP or with the Ubuntu 7.10 LiveCD either.
I'm thinking hardware problem if it won't work in multiple OS's. Put a different network card in and see what you get. I've seen hardware fail many times where the LED indicators continued to function, thus disguising the failure as misconfiguration.

> **blastus said:**
>  Tomorrow I'll try hooking this computer up to another computer and see if I can ping it. If that works then I'll reset my router--I think it clears out everything on it which is different than just unplugging it and plugging it back in again. I was thinking that maybe the router has blacklisted the MAC addresses (if that's possible maybe it thinks the MAC is spoofed I don't know) of the network cards I tried or something...maybe the host name has to be unique on the network (I've tried changing the host name on the computer as it was the same as a wireless computer on my network, but that didn't fix the issue.) 
Unique hostname would definitely help. If your other boxes can access the internet just fine, then it's very likely *not* your router or modem. I've also seen a trashed /etc/hosts file prevent networking due to hostname issues. Might want to check that. If you need a "fresh" hosts file, I can post the contents of one.

> **blastus said:**
>  Thanks a lot for all your help!
You're welcome. 

-------------------------------------------------------------------------------------

> **Cristinalee said:**
> There is often problems with my computer .So i hope you can help me solve the problems.
I'd be glad to help if you start your own thread, though you will need to be much more specific about the nature of your problems.

NOTE: When you start your own thread, be sure to give it a useful, descriptive title. This will ensure you get the best, fastest, most accurate help we can provide. Some people won't bother to look at your post if they can't tell what it's about from the title.
Thread title examples:
**Bad:** 
I need Help with my PC
My comp has problems, please help.
**Worst:**
Pleaseeeeee HEEEELLLLP!!!!!
**Good:**
No networking in Ubuntu Gutsy
DWA-542 wireless Desktop adapter Trouble
Dlink DWA-542 Atheros AR5416/ a/g/n/b Wifi Card

By posting here, you're hijacking blastus' thread, which is kind of like interrupting a conversation or cutting line in the real world.

---

