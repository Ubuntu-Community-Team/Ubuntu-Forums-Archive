---
title: "[SOLVED] Wireless networking doesn't start on boot, only after login."
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by peterc26 on 2007-11-03
I've recently installed Gutsy (fresh install) and I'm unable to get the wireless networking to start automatically on boot.  It's fine once I've logged in though.

Network Manager says it's using the rt61pci driver. 
/etc/network/interfaces just contains:

```

auto lo
iface lo inet loopback

```

Once it's up and running, ifconfig says:

```

eth0      Link encap:Ethernet  HWaddr 00:18:F3:19:93:27  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:461 (461.0 b)  TX bytes:461 (461.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:BD:EA:2D  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:febd:ea2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1848517 (1.7 MB)  TX bytes:461038 (450.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-BD-EA-2D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

It all used to worked fine on Feisty.  I've had a look through dmesg log but I can't find anything that explains the problem (although I don't really know what I'm looking for !)

I tried Wicd which DID start on boot, but unfortunately I then had a separate problem with getting the Firestarter firewall to start up automatically before login.

(Incidentally, I'm also getting the problem that a lot of other people seem to be getting where the connection drops after a while, particularly when it's doing large downloads, but that's another problem !)

Thanks in advance for any suggestions.

Peter.

---

### Post by mrvertigo on 2007-11-03
mmm why on earth would you need a connection before you are logged in on a wireless connect? I could see a hardwired reason (file/ftp/web server) but on wireless?

---

### Post by peterc26 on 2007-11-03
I sometimes access my PC remotely, and also I access its files and printer across my network from a Windows laptop.

The reason for wireless is simply because my PC is across the other side of my lounge from the telephone point where I get my broadband, and I don't want to run any wires ! 

It did all work fine under Feisty, but I just can't seem to crack it on Gutsy.

---

### Post by ricklous on 2007-11-03
Im in the same boat...

Im wanting the wireless connection pre logon due to it being a rented house and being unable to rewire it to my liking - so Im stuck with wireless -  and Im trying to automate an overnight backup routine.

So, I'd like my ubuntu box to fire up at 1am, connect to the wireless network, do the backup and whatever other adhoc transfers Ive set up to run over night (like syncing my podcasts to my phone if its plugged into the USB and charging) and then go to sleep again. Everything works fine, theres an alarm set in bios to fire the PC up, the cron job works just fine if Im logged in, and it shuts down fine. The missing piece of the jigsaw is the wireless network connecting 'seamlessly' without me being there.

So, any help trying to get the wireless up and running without user intervention would be very nice :)

Is this something to do with the WPA password being in the keyring?

---

### Post by rtg on 2007-11-03
I've posted my solution/workaround here - could you please check if it helps you:
[http://ubuntuforums.org/showthread.php?p=3679330](http://ubuntuforums.org/showthread.php?p=3679330)

---

### Post by peterc26 on 2007-11-04
Thanks for the suggestion, rtg, but no luck I'm afraid.

---

### Post by peterc26 on 2007-11-04
I think my problem is the same as pug's in this thread:-

[http://ubuntuforums.org/showthread.php?t=598880](http://ubuntuforums.org/showthread.php?t=598880)

It sounds likely that the root of the problem is the Network Manager storing the WPA password in the keyring, which isn't accessible until you've logged in.

---

### Post by peterc26 on 2007-11-04
:)  I've managed to solve my problem by changing my driver from Gutsy's rt61pci to Ralink's rt61.  In doing so, I no longer use Network Manager to enter my WPA key, but instead it is configured in a separate config file for the driver (namely /etc/Wireless/RT61STA/rt61sta.dat).  

So now the network successfully starts during bootup.  I've also uninstalled network-manager-gnome because it is of no use to me now.

Hopefully, this will also solve my problem of my network connection dropping intermittently.

For reference, I followed the How To on:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

---

