---
title: "No connection. Wireless or ethernet."
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by upmoist on 2007-10-21
I've been running Fedora on this laptop since it was new and
the ethernet and wireless work great.  I decided weeks ago that
when Ubuntu Gutsy came out I would make the switch.  I did
just that, completely wiping out and starting over and now I
have no networking at all.  Neither eth0 nor wlan0. Here's my
configuration:
   
   Make/Model	Averatec 3250
   Ethernet		VIA VT6102 [Rhine II]
   Wireless		RaLink RT2500 802.11g Cardbus/mini-PCI
   
For the wireless under, that older, Fedora I had to build and
install the model from rt2x00.serialmonkey.com for each kernel.
After installing Gutsy everything looked great!  I clicked on
the NetworkManager icon and, amazingly, it saw all the local
wireless networks automagically.  Sweet!

That's where the problems started.  I could not seem to connect
to any of them.  Then I connected the cat5 cable and could not
hook up with even the wired network.  Even putting in a known
IP address wouldn't work.  I am disconnected.  I've worked on
this at a few locations where I controlled everything including
the dhcp servers.  Now I'm ready to ask for help.

Let's start with the eth0 connection because I would guess
that the problems with wireless are related.  I'm at home with
an older dlink which I have been using for years and I boot up
with both wired connected and wireless.  I click the NetMngr
icon and see wireless accesspoints including my own.  Going
to "manual configuration" I select the "wired connection"
and configure it to "Automatic configuration (DHCP)" where
it proceeds to never make a connection.

Let's do it manually and see what's happening.  Any help
will be greatly appreciated...

ifconfig eth0
```

eth0      Link encap:Ethernet  HWaddr 00:40:45:24:CA:84  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:679 overruns:0 frame:0
          TX packets:25 errors:9 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4452 (4.3 KB)  TX bytes:3450 (3.3 KB)
          Interrupt:11 Base address:0xd800 

```

ifup eth0
```

There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:40:45:24:ca:84
Sending on   LPF/eth0/00:40:45:24:ca:84
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
Ah, it said dhcp no offers but it did recieve an offer.
more /var/lib/dhcp3/dhclient.leases
```

lease {
  interface "eth0";
  fixed-address 192.168.0.103;
  option subnet-mask 255.255.255.0;
  option routers 192.168.0.1;
  option dhcp-lease-time 604800;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.0.1;
  option domain-name-servers 192.168.0.1;
  renew 0 2007/10/21 06:08:54;
  rebind 0 2007/10/21 06:08:54;
  expire 0 2007/10/21 06:08:54;
}

```
ifconfig eth0
```

eth0      Link encap:Ethernet  HWaddr 00:40:45:24:CA:84  
          inet6 addr: fe80::240:45ff:fe24:ca84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:679 overruns:0 frame:0
          TX packets:25 errors:14 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4452 (4.3 KB)  TX bytes:3450 (3.3 KB)
          Interrupt:11 Base address:0xd800 

```
Even when I tried to shut it down it tried to give the 'offer' back to the correct IP.
ifdown eth0
```

There is already a pid file /var/run/dhclient.eth0.pid with pid 5842
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:40:45:24:ca:84
Sending on   LPF/eth0/00:40:45:24:ca:84
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67

```

---

### Post by Laerte Andrade on 2007-10-25
> I've been running Fedora on this laptop since it was new and
the ethernet and wireless work great. I decided weeks ago that
when Ubuntu Gutsy came out I would make the switch. I did
just that, completely wiping out and starting over and now I
have no networking at all. Neither eth0 nor wlan0.

A friend of mine has exactly the same laptop as you (Averatec 3250). Yesterday he installed Ubuntu Gutsy Gibbon (7.10) and both ethernet and wireless were not working. We managed to correct this by doing two things:

First, you have to add **acpi=noirq** to /boot/grub/menu.lst after your kernel of choice:

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=31480cee-943d-4777-85b8-56a9825614c8 ro **acpi=noirq** quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
```


This should resolve the issues with ethernet. After that, we configured the wireless card by following the instructions (to the letter) in this thread:

[http://ubuntuforums.org/showthread.php?t=584657&highlight=rt2500](http://ubuntuforums.org/showthread.php?t=584657&highlight=rt2500)

That's it. After looking for some information about Ubuntu in this particular laptop, I noticed that this problem was corrected in Feisty (7.04), but came back in Gutsy. It is a shame really.

---

### Post by salefish on 2007-10-29
I have the same Averatec 3250 with the identical problem. It shows all the wireless access poin ts but will not connect, and the Ethernet connection doesn't work either. 
I am not as advanced as either of you two seem to be with Ubuntu, or Linux as a whole. Is there anyway that you can post specific instructions on how to get the Ethernet working?
When I go to either the terminal or navigate to it through the graphical file system, it says permission denied.

---

