---
title: "No Network Connection"
date: 2005-05-14
forum: Networking &amp; Wireless
---

### Post by OneMan on 2005-05-14
sigh. I'm tired. Hoary does not want me on the internet.
Warty worked fine, Hoary livecd worked fine. Even during the installation of hoary it setup the internet connection fine, I noticed the lights on my modem blinking away at one stage.
But when I actually boot into hoary. nothing.  ](*,) I don't really have a clue, but dhcp-client seems to fail and go to sleep?
I've been looking for a solution for ages. So what do I do? Whats the easy fix that I haven't noticed?

Thanks, Steve

---

### Post by alastair on 2005-05-14
You could start by giving us some vaguely useful information to go on e.g.

 - describe your network and network h/w
 - describe how things are connected and how you get on the internet
 - check /var/log/syslog for networking device messages (e.g. network driver load, eth* etc.)

outputs of :

ifconfig -a
route -n

Anything else of use ...

---

### Post by OneMan on 2005-05-14
yeah, sorry for not giving much info.
I'm using a dlink 4 port router
for outputs of stuff will have to wait until i boot into ubuntu again
Is it at all useful that I've had to turn off ipv6 in /etc/modprobe/aliases to get around really slow dns lookup times in every distro i've used? thats the only other networking problem I've ever had with other distros.

---

### Post by OneMan on 2005-05-14
ifconfig -a
> eth0      Link encap:Ethernet  HWaddr 00:08:A1:27:47:C9  
          inet6 addr: fe80::208:a1ff:fe27:47c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3798 (3.7 KiB)
          Interrupt:17 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68564 (66.9 KiB)  TX bytes:68564 (66.9 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
 route -n was empty except for column headings
And here is a few bits and pieces that I thought may be relevant from the syslog
driver info yes?
> May 15 00:46:07 localhost kernel: Linux Tulip driver version 1.1.13 (May 11, 2002)
May 15 00:46:07 localhost kernel: ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 17
May 15 00:46:07 localhost kernel: tulip0:  MII transceiver #1 config 1000 status 782d advertising 01e1.
May 15 00:46:07 localhost kernel: eth0: Davicom DM9102/DM9102A rev 64 at 0001cc00, 00:08:A1:27:47:C9, IRQ 17.
May 15 00:46:07 localhost kernel: dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
some random stuff I noticed> May 15 00:46:25 localhost kernel: NET: Registered protocol family 10
May 15 00:46:25 localhost kernel: Disabled Privacy Extensions on device c02f0500(lo)
May 15 00:46:25 localhost kernel: IPv6 over IPv4 tunneling driver
May 15 00:46:31 localhost gconfd (stephen-7696): Resolved address "xml:readwrite:/home/stephen/.gconf" to a writable configuration source at position 0
May 15 00:46:35 localhost kernel: eth0: no IPv6 routers present 
and dhcp goes to sleep> 
May 15 00:48:53 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 15 00:48:56 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 15 00:49:03 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 15 00:49:15 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
May 15 00:49:29 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
May 15 00:49:48 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 15 00:49:54 localhost dhclient: No DHCPOFFERS received.
May 15 00:49:54 localhost dhclient: No working leases in persistent database - sleeping.


---

### Post by kleeman on 2005-05-14
This sounds a lot like this bug

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8086](https://bugzilla.ubuntu.com/show_bug.cgi?id=8086)

which applies to hoary and not warty.
There seems to be a possible workaround at the bottom of the page
and also some annoyed responses from developers ;-)

---

### Post by OneMan on 2005-05-14
[QUOTE=kleeman]This sounds a lot like this bug

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8086](https://bugzilla.ubuntu.com/show_bug.cgi?id=8086)

which applies to hoary and not warty.
There seems to be a possible workaround at the bottom of the page
and also some annoyed responses from developers ;-)[/QUOTE]
 It does sound a lot like that bug. But I don't know about the work around suggested.
I added pci=noacpi to the kernel line of the grub boot command thingo, and still nothin.
Thats what I was meant to do yes?
Ahh well, bed time.

---

### Post by kleeman on 2005-05-14
Perhaps you should add your experience and diagnostic files to this bug to put more pressure on the devs to fix up dhcp

---

