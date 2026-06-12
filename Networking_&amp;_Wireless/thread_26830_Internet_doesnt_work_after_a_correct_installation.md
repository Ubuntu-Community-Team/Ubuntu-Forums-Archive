---
title: "Internet doesnt work after a correct installation"
date: 2005-04-14
forum: Networking &amp; Wireless
---

### Post by elmandelsaco on 2005-04-14
Thats the main issue: I have installed Ubuntu 5.04 on my Acer notebook 1601LC and all was ok. The installation process did actually download some packages (language mostly) but after all installation, Internet doesnt work.

My ISP has DHCP server, and my ubuntu gets IP and DNS servers and stuff, but i cant browse, send pings, or trace a route.

All devices are installed and working fine (i think so), and ifconfig says my interface is working well... I'm really confused.

One more thing...if i'm working on my ubuntu and then i restart windows, the clock in windows has changed and it shows 2 hours less than it should show. I think i have to run base-config and say the system that my clock is not synched to hardware clock...
am i right??

Thanks.

---

### Post by chambs10 on 2005-04-14
elmandelsaco,

You are correct with the hardware clock settings. You might want to run the base setup and configure the clock not to run with the hardware (UTM).  Alternatively, you can set up a time server synch with both Linux and Windows.  My assumption is that you are synching with an NTP time server through linux (which of course you cannot get to right now because your network is down). You can setup NTP with windows as well. The first link is a long description of how to set up NTP in windows, followed by the second link which is a list of microsoft affiliated NTP servers.

[http://www.windowsnetworking.com/articles_tutorials/Configuring-Windows-Time-Service.html](http://www.windowsnetworking.com/articles_tutorials/Configuring-Windows-Time-Service.html)
[http://support.microsoft.com/default.aspx?scid=kb;EN-US;q262680](http://support.microsoft.com/default.aspx?scid=kb;EN-US;q262680)

As far as you network card I have a couple questions.  When the machine boots up does the system give you any warning about eth0? Can you still connect via win?  I'm just trying to cover the simple steps first...running through the layers. It is possible the network is down.

Peace Out.

---

### Post by elmandelsaco on 2005-04-14
Hey, thanks buddy...this help forum really works!!

Well, since we have solved the clock problem, lets fix my network (please!! lol)

While machine is booting, i dont receave any warning, thats the funny thing, and of course network works in windows.

Thats the reason i'm fully confused.

Thank you again.

---

### Post by eutu on 2005-04-14
I have the same problem cannot connect to internet the dhcp is getting all the info from the provider  but not able to ping. I had the same problem with time I fixed it by enabling the daylights saving time.

---

### Post by az on 2005-04-14
Is there anything in dmesg about your network card?

---

### Post by eutu on 2005-04-14
i get this mesage when i run  dmesg  
no IPv6 routers present
when i open the dhclient.conf i get
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, net-scope, interface-mtu;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject xxx.xx.xxx.xxx;

#alias {
#  interface "eth0";
#  fixed-address xxx.x.x.xxx;
#  option subnet-mask xxx.xxx.xxx.xxx;
#}

#lease {
#  interface "eth0";
#  fixed-address xxx.xx.xxx.xxx;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask xxx.xxx.xxx.x;
#  option broadcast-address xxx.xx.xxx.xxx;
#  option routers xxx.xx.xxx.xxx;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
every thing works fine under windows and fadora core 3

---

### Post by alastair on 2005-04-14
Describe your network setup e.g. DSL? USB modem? ethernet modem? PPP? etc. Detail!

Check the logs when you boot : /var/log/syslog

Look for relevant lines relating to networking e.g. ethernet (eth?), or perhaps USB devices etc. Depending on your h/w and config.

For interface issues :

ifconfig -a
route -n

Plus gateway details perhaps (if neccessary).

More info basically ....

---

### Post by mila80 on 2005-04-15
I have the same problem since I have upgraded from 4.10 to horay...

---

### Post by eutu on 2005-04-15
I have a cable modem pluged into the ethernet card during install it said that it succesfuly configured dhcp. During boot it gets to the configure network part and sits there for about 1\2 minute then finishes booting but does not give a fail.

---

### Post by elmandelsaco on 2005-04-15
then i guess i give up with my problem :(

---

### Post by kleeman on 2005-04-15
Oh come on! Follow alastair's advice... Linux sometimes requires patience  :smile:  :smile:  :smile:

---

### Post by elmandelsaco on 2005-04-15
Here you got some info:


pableras@thugmobile:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:42:27:34
          inet addr:10.16.42.120  Bcast:10.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe42:2734/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17439 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:91 txqueuelen:1000
          RX bytes:24775631 (23.6 MiB)  TX bytes:588301 (574.5 KiB)
          Interrupt:19 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2331972 (2.2 MiB)  TX bytes:2331972 (2.2 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

pableras@thugmobile:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.16.42.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         10.16.42.1      0.0.0.0         UG    0      0        0 eth0

pableras@thugmobile:~$ dmesg
/target0/lun1: unknown partition table
Attached scsi removable disk sdb at scsi0, channel 0, id 0, lun 1
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9008a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9208a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9208a03c.
eth0:  Tx descriptor 3 is 9008a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9108a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9308a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9408a03c.
eth0:  Tx descriptor 3 is 9008a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9108a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9308a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9208a03c.
eth0:  Tx descriptor 3 is 9408a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9108a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9208a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9108a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9108a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9208a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9208a03c.
eth0:  Tx descriptor 3 is 9008a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9208a03c.
eth0:  Tx descriptor 3 is 9008a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9208a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9308a03c.
eth0:  Tx descriptor 3 is 9008a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9208a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9308a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
irq 19: nobody cared (try booting with the "irqpoll" option.
 [<c012e4cb>] __report_bad_irq+0x31/0x77
 [<c012e59e>] note_interrupt+0x75/0x9b
 [<c012df82>] __do_IRQ+0xd3/0x111
 [<c0104cc5>] do_IRQ+0x19/0x24
 [<c0103966>] common_interrupt+0x1a/0x20
handlers:
[<d0ad4a3b>] (rtl8139_interrupt+0x0/0x162 [8139too])
Disabling IRQ #19
eth0: no IPv6 routers present
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
irq 19: nobody cared (try booting with the "irqpoll" option.
 [<c012e4cb>] __report_bad_irq+0x31/0x77
 [<c012e59e>] note_interrupt+0x75/0x9b
 [<c012df82>] __do_IRQ+0xd3/0x111
 [<c0104cc5>] do_IRQ+0x19/0x24
 [<c0103966>] common_interrupt+0x1a/0x20
handlers:
[<d0ad4a3b>] (rtl8139_interrupt+0x0/0x162 [8139too])
Disabling IRQ #19
eth0: no IPv6 routers present
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 7  dirty entry 3.
eth0:  Tx descriptor 0 is 9008a046.
eth0:  Tx descriptor 1 is 9008a046.
eth0:  Tx descriptor 2 is 9008a156.
eth0:  Tx descriptor 3 is 9008a156. (queue head)
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a156. (queue head)
eth0:  Tx descriptor 1 is 9008a156.
eth0:  Tx descriptor 2 is 9008a156.
eth0:  Tx descriptor 3 is 9008a156.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a156. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9008a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
irq 19: nobody cared (try booting with the "irqpoll" option.
 [<c012e4cb>] __report_bad_irq+0x31/0x77
 [<c012e59e>] note_interrupt+0x75/0x9b
 [<c012df82>] __do_IRQ+0xd3/0x111
 [<c0104cc5>] do_IRQ+0x19/0x24
 [<c0103966>] common_interrupt+0x1a/0x20
handlers:
[<d0ad4a3b>] (rtl8139_interrupt+0x0/0x162 [8139too])
Disabling IRQ #19
eth0: no IPv6 routers present
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 5  dirty entry 1.
eth0:  Tx descriptor 0 is 9008a046.
eth0:  Tx descriptor 1 is 9008a04e. (queue head)
eth0:  Tx descriptor 2 is 9008a046.
eth0:  Tx descriptor 3 is 9008a046.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9108a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9108a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9208a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9408a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9208a03c.
eth0:  Tx descriptor 3 is 9008a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9108a03c.
eth0:  Tx descriptor 3 is 9308a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9208a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9208a03c.
eth0:  Tx descriptor 3 is 9008a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9108a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9108a03c.
eth0:  Tx descriptor 3 is 9108a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9008a03c.
eth0:  Tx descriptor 3 is 9308a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
NETDEV WATCHDOG: eth0: transmit timed out
eth0: Transmit timeout, status 0c 0005 c07f media 18.
eth0: Tx queue start entry 4  dirty entry 0.
eth0:  Tx descriptor 0 is 9008a03c. (queue head)
eth0:  Tx descriptor 1 is 9008a03c.
eth0:  Tx descriptor 2 is 9108a03c.
eth0:  Tx descriptor 3 is 9008a03c.
eth0: link up, 10Mbps, half-duplex, lpa 0x00

pableras@thugmobile:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memor y & AGP Controller (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bri dge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media I O] (rev 14)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Con troller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev  a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound  Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:00:09.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controlle r (rev 01)
0000:00:09.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controlle r (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Rad eon Mobility 9000 M9] (rev 01)
0000:06:00.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference C ard (rev 01)
pableras@thugmobile:~$

---

### Post by kleeman on 2005-04-15
dmesg is obviously showing problems.
after googling on the error message. My guesses are:
1) Either the nic is a bit flakey (does warty work?)
2) There is a driver problem

Anyone else have any ideas?

---

