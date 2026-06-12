---
title: "Gaim or Kopete drop internet connection"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by impuwat on 2007-08-09
Over the last several years I've attempted the transition from Windows to Ubuntu/Xubuntu several times on several different machines with varying success.  I would love to make the transition complete but have been thwarted each time by various problems I couldn't solve.  I'm very close with this attempt and am excited about the possibilities.

I have Xubuntu installed and running but have struggled with a weak, intermittent internet connection.  I have a wireless IP.   The wireless antenna feeds a switch, which I have connected to a PCI ethernet card.  Xubuntu boots up with internet.  As long as I actively surf the net the connection seems to be solid.  If I stop surfing for a time I loose the connection.  If I switch to Synaptic and back to my browser, I usually loose the connection.  The only way to restore the internet is a complete shutdown and startup.  A restart does not restore the connection.  If I have a connection and try to start Gaim or Kopete the connection is immediately severed and Gaim fails to connect.

Windows pc's hooked to the same cable work flawlessly, and I run one WinXP machine on a Linksys wireless hooked into the same switch.

I initially suspected a bad PCI ethernet card and switched that out with no change in performance.

Here is a little output to ponder:

lspci -nn

> 00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] [1106:0691] (rev c4)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP] [1106:8598]
00:07.0 ISA bridge [0601]: VIA Technologies, Inc. VT82C686 [Apollo Super South] [1106:0686] (rev 22)
00:07.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 10)
00:07.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 10)
00:07.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 10)
00:07.4 Host bridge [0600]: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] [1106:3057] (rev 30)
00:07.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT82C686 AC97 Audio Controller [1106:3058] (rev 20)
00:0c.0 Ethernet controller [0200]: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 [1317:0985] (rev 11)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 MX 440] [10de:0171] (rev a3)


sudo lshw -C network

> 00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] [1106:0691] (rev c4)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP] [1106:8598]
00:07.0 ISA bridge [0601]: VIA Technologies, Inc. VT82C686 [Apollo Super South] [1106:0686] (rev 22)
00:07.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 10)
00:07.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 10)
00:07.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 10)
00:07.4 Host bridge [0600]: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] [1106:3057] (rev 30)
00:07.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT82C686 AC97 Audio Controller [1106:3058] (rev 20)
00:0c.0 Ethernet controller [0200]: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 [1317:0985] (rev 11)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 MX 440] [10de:0171] (rev a3)


ifconfig -a

> eth1      Link encap:Ethernet  HWaddr 00:0C:41:E5:84:BF  
          inet addr:192.168.1.152  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:fee5:84bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1282362 (1.2 MiB)  TX bytes:411586 (401.9 KiB)
          Interrupt:11 Base address:0x7c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13700 (13.3 KiB)  TX bytes:13700 (13.3 KiB)


cat /etc/network/interfaces

> auto eth0
iface eth0 inet dhcp
address 192.168.1.153
netmask 255.255.255.0
gateway 192.168.1.1


iface eth1 inet dhcp
address 192.168.1.152
netmask 255.255.255.0
gateway 192.168.1.1



iface rausb0 inet static
wireless-essid linksys
address 192.168.1.152
netmask 255.255.255.0
gateway 192.168.1.1


I would really appreciate any help to solve this problem.

respectfully................Jerry

---

### Post by lucazade on 2007-08-10
I've got the same problem, also using a wired connection. All the msn clients I tried lose connection after some minutes and I don't know how to solve...

Is there any log-activities for the tcp internet connection?
I've tried with and w/o firewall, full reinstall, dhcp and static ip,behind a router, new lan cable, disabling ipv6.. :confused:
Is it useful to modify resolv.conf or use a opendns? 

help!
(sorry for my english)

---

### Post by impuwat on 2007-08-10
I tried the suggestions in all of the threads listed below....to no avail.  Erratic network problem still continued.

[http://ubuntuforums.org/showthread.php?t=394067](http://ubuntuforums.org/showthread.php?t=394067)

[http://ubuntuforums.org/showthread.php?t=317143](http://ubuntuforums.org/showthread.php?t=317143)

[http://ubuntuforums.org/showthread.php?t=206411](http://ubuntuforums.org/showthread.php?t=206411)

[http://ubuntuforums.org/showthread.php?t=474681](http://ubuntuforums.org/showthread.php?t=474681)

Finally decided the problem was either an undiagnosed problem with Xubuntu or my hardware.  For the next step I downloaded the Kubuntu 7.04 live cd.  **Kubuntu worked flawlessly** in the live cd so I've decided to install Kubuntu and do further testing. I was able to log on to Kopete and surf the net and back and forth with no loss of network. 

 It appears to be some problem with Xubuntu that no one has been able to figure out and just crops up periodically with unlucky people like me!  I will post more after I have Kubuntu loaded and tested.  My RAM is borderline for Kubuntu so I might be exchanging one problem for others.:)

---

