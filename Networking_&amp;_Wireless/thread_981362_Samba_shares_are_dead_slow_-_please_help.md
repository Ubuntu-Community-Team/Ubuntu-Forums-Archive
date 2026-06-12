---
title: "Samba shares are dead slow - please help"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by zabby on 2008-11-13
Hey all,

I'm trying to figure out what could be wrong with my samba shares.  Even when I'm copying single, large files on to a mostly empty drive it only ever seems to top out at 300Kbytes a second!  My internet speeds on my windows desktop are faster than that :-(.  This is a problem for both my raid array and the old NTFS formatted drive I have in there.  When I switch my dual boot machine to windows the problem goes away.

---

### Post by dmizer on 2008-11-13
Try physically mounting your shares via /etc/fstab as outlined in the CIFS howto (second link) in my sig.

---

### Post by zabby on 2008-11-14
Thanks for the help.  Unfortunately the problem persists :(.  Any other ideas?  This is really frustrating.

---

### Post by dmizer on 2008-11-14
> **zabby said:**
> Thanks for the help.  Unfortunately the problem persists :(.  Any other ideas?  This is really frustrating.

Your problem is something more fundamental than CIFS then. When mounting with /etc/fstab, it will still be a bit slower than what Windows can accomplish, but it should be tolerable.

What kind of network interface are you using (wireless, wired, chipset, model etc)?

---

### Post by zabby on 2008-11-14
Thanks a lot for your responses.  I'm using a wired 100mbps network w/ a VIA Rhine III Fast Ethernet Controller chip.

---

### Post by dmizer on 2008-11-14
Please post the output of the following two commands:
```
sudo ifconfig
```
and
```
lshw -C network
```
Are other speeds acceptable? Browsing the internet or ftp file transfer for example?

---

### Post by opt1k on 2008-11-15
I also encountered this problem.
Its not only the Samba shares.  Also FTP transfers from the system running ubuntu. Probably also HTTP.

The problem is related to a buggy network driver. Try using ndiswrapper and the windows driver for your network interface.

---

### Post by zabby on 2008-11-16
Thanks for the replies!  I'll try ndiswrapper tomorrow (would be nice to get it working the "proper" way though).  Here is the requested output.

**sudo ifconfig**
```

eth0      Link encap:Ethernet  HWaddr 00:40:63:D9:83:78  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:63ff:fed9:8378/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:132584 (129.4 KB)  TX bytes:2496095 (2.3 MB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:448 (448.0 b)  TX bytes:448 (448.0 b)

```

**lshw -C network**
```

  *-network:0             
       description: Ethernet interface
       product: VT6105 [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: 8b
       serial: 00:40:63:d9:83:78
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.5 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s

  *-network:1 DISABLED
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 74
       serial: 00:40:63:d9:83:3c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s


```

---

### Post by dmizer on 2008-11-16
No need to try Ndiswrapper. You're not running wireless.

Try disabling IPv6 according to these directions: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Are you running a firewall either on the Windows machine or on the Ubuntu machine?

---

### Post by zabby on 2008-11-16
Oh... sorry forgot to answer one of your questions...  I did try FTP and I got 40 megabits / sec...  so it seems to be constrained to Samba?

Knocked off IP6, problem still persists.

---

### Post by dmizer on 2008-11-16
> **zabby said:**
> Oh... sorry forgot to answer one of your questions...  I did try FTP and I got 40 megabits / sec...  so it seems to be constrained to Samba?

Knocked off IP6, problem still persists.

What kind of server are you connecting to? You said you tried mounting via CIFS and it was still slow. What was your /etc/fstab mount line?

---

### Post by zabby on 2008-11-25
Sorry for the lag in responses!  I'm back now.

I'm mounting with the following command:

mount -t cifs //192.168.1.5/Dump /media/Dump -o username=XXXXX,password=XXXXXX

The server is either a Windows XP box, or a Linux Ubuntu 8.10 box (depending).

---

### Post by randomtask742 on 2009-01-07
Hi - I'm a new member to the Ubuntu forums, but have long been a strong supporter.

I am having the EXACT same problem as documented here, and in MANY other threads:

I have an xp desktop and a Linux laptop.  On my laptop, when I connect to the XP comp using smb://[ip], i get transfer speeds around 500Kb/sec.  Terrible!  I have tried many configurations of socket options (e.g. TCP_NODELAY, and others) to no avail.

To give an idea of my network hardware here is an excerpt from the command 'lspci':

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
06:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

This have been so many users who have cronicled their problem, I hope there's an answer out there.  Many thanks!

RT

---

### Post by onesojourner on 2009-01-14
I am having problems with this too. My speeds are about the same as a slow dial up connection, 2.2KB. I am trying to transfer files from a 8.04 machine to a freshinstall of 8.10. both machines are running g wireless cards.

---

