---
title: "Netgear GA311 Not Found"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by brooky on 2007-03-12
I've installed a Netgear GA311 into my Dell server today. I was under the impression it would be discovered and work straight away.

If I type ifconfig in the terminal it returns:> eth0      Link encap:Ethernet  HWaddr 00:13:20:47:AE:72
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe47:ae72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20672 (20.1 KiB)  TX bytes:57900 (56.5 KiB)
          Interrupt:169

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


eth0 is the integrated card. If I press F2 on boot and disable it ifconfig only returns:> lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Have I done something wrong?

I'm running Ubuntu Server 6.10. Should I donwload and install the drivers from the realtek site?

---

### Post by chili555 on 2007-03-12
Please do sudo modprobe 8139too. Then check ifconfig and see if eth0 shows up. If so, then try sudo ifup eth0. Let us know.

---

### Post by brooky on 2007-03-12
Thanks a million for your reply. 

> al@office:~$ sudo modprobe 8139
FATAL: Module 8139 not found.
al@office:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:47:AE:72
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe47:ae72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:887 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:67681 (66.0 KiB)  TX bytes:165519 (161.6 KiB)
          Interrupt:169

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


---

### Post by chili555 on 2007-03-12
It's 8139**too**.

Also, it looks like your onboard card is enabled. Did you intend to use both somehow? If not, you'll need to go into the BIOS and disable your onboard nic. If so, the GA311 may show up as eth1.

Please try again.

---

### Post by brooky on 2007-03-12
Hello again. :)

I disabled the onboard ethernet adapter in the BIOS. Then I rebooted and run the following commands:

> al@office:~$ sudo modprobe 8139too
FATAL: Module 8139too not found.

> al@office:~$ ifconfig

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

---

### Post by chili555 on 2007-03-12
Gosh! How old is the kernel in that machine? After a sudo updatedb (takes some time), locate 8139 on my machine produces, in part: ```
chili@LAPTOP:~$ locate 8139
/lib/modules/2.6.17-10-generic/kernel/drivers/net/8139cp.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/8139too.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/net/8139cp.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/net/8139too.ko
```

You can find out the version of your running kernel with uname -r

---

### Post by brooky on 2007-03-12
Odd I get exactly the same result as you except from the fact I run server edition:

> locate 8139
/lib/modules/2.6.17-10-server/kernel/drivers/net/8139cp.ko
/lib/modules/2.6.17-10-server/kernel/drivers/net/8139too.ko
/lib/modules/2.6.17-11-server/kernel/drivers/net/8139cp.ko
/lib/modules/2.6.17-11-server/kernel/drivers/net/8139too.ko

I'm running kernel v 2.6.17-11-server

Is there anything else I can try?

---

### Post by chili555 on 2007-03-12
OK, now it's time to get serious! Into the warp core!

Let's take a look at lsmod | grep 8139, lspci -v | grep Ethernet,  as well as dmesg | grep 8139. Please type carefully.

---

### Post by brooky on 2007-03-12
Here it comes.... :)

```
al@office:~$ lsmod
Module                  Size  Used by
ipv6                  271136  20
af_packet              24584  2
lp                     12964  0
r1000                  17920  0
r8169                  32264  0
sg                     37020  0
tg3                   108036  0
pcspkr                  4352  0
parport_pc             37796  1
parport                39368  2 lp,parport_pc
evdev                  11392  0
psmouse                41352  0
serio_raw               8452  0
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
ext3                  142600  1
jbd                    62100  1 ext3
ide_generic             2432  0
ehci_hcd               35208  0
uhci_hcd               25096  0
usbcore               134656  3 ehci_hcd,uhci_hcd
sd_mod                 22528  3
3w_xxxx                28960  2
ata_piix               11780  0
ahci                   20356  0
libata                 74764  2 ata_piix,ahci
scsi_mod              144392  5 sg,sd_mod,3w_xxxx,ahci,libata
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
piix                   11780  1
generic                 6276  0
thermal                15624  0
processor              31560  1 thermal
fan                     6020  0
fbcon                  41376  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability
```

```
al@office:~$ grep 8139, lspci -v
grep: lspci: No such file or directory
```

"grep Ethernet", "grep dmesg" and "grep 8139"  seem to make it hang. Am I typing wrong? :-/

---

### Post by chili555 on 2007-03-12
Yessir. Use that little pipe symbol on your keyboard above the frontslash \. The pipe | means pipe the command through another command. So, lsmod | grep 8139 means list all the inserted modules, but then grep, or look for a pattern 8139. It is not there, so the prompt would have popped back empty. 

I notice r8169 is there, so perhaps your card is the RTL8169. We shall find out!

Try: ```

lspci -v | grep Ethernet
dmesg | grep 8169
```

Thanks.

---

### Post by brooky on 2007-03-12
Ooooh it sees it! Its the Realtek chipset one. The Broadcom one is the integrated 10/100 one.
```
al@office:~$ lspci -v | grep Ethernet
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

```
al@office:~$ dmesg | grep 8169
[42949399.410000] r8169 Gigabit Ethernet driver 2.2LK loaded
[42949399.410000] eth1: Identified chip type is 'RTL8169s/8110s'.
[42949399.410000] eth1: RTL8169 at 0xe0060f00, 00:18:4d:76:a9:d1, IRQ 50
```

Does it have something to do with my interfaces file?

>  This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


---

### Post by chili555 on 2007-03-12
Almost there...

sudo gedit /etc/network/interfaces to add eth1 listings like this: ```
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

Take out auto eth0, but not the rest of eth0's wordings, if it's there. Save and close. Restart networking by doing sudo /etc/init.d/networking restart and see if it takes off.

I will be consulting a qualified religious professional.

---

### Post by brooky on 2007-03-12
Sorry I was being stupid!! Testing... think it's worked!!

Will get back to you in a sec....

---

### Post by brooky on 2007-03-12
Hmm... right ok I put the file as:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

Then ran sudo /etc/init.d/networking restart and a whole load of data was displayed concerning the cards. Like so:```
al@office:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 3489
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:13:20:47:ae:72
Sending on   LPF/eth0/00:13:20:47:ae:72
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:13:20:47:ae:72
Sending on   LPF/eth0/00:13:20:47:ae:72
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.3 -- renewal in 102135 seconds.
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:18:4d:76:a9:d1
Sending on   LPF/eth1/00:18:4d:76:a9:d1
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
Trying recorded lease 192.168.0.11
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 2.884/2.884/2.884/0.000 ms
bound: renewal in 123828 seconds.
                                                                         [ ok ]

```

Now I can't connect through either. I expect it might be to do with IP adress reservation on the  router with MAC code... Will experiment.

Thanks so much for your help. Hopefully we are there now......

---

### Post by chili555 on 2007-03-12
Don't think you will readily connect two interfaces with two IP addresses. Please detach the cable from the onboard and try again.

---

### Post by brooky on 2007-03-12
Hooooooooooray!! It works!!

Will you marry me? :guitar:

Thanks for all your help you are extremely kind and I am very much apreciative.

*Edit* Wierd?!?! It seems to stop working after a bit of time. I wonder whether "iface eth1 inet dhcp" should be "iface eth1 inet6 dhcp". I have to leave the office now but I'll look at this again tomorrow. Thanks again.

---

### Post by chili555 on 2007-03-12
Woo-hoo! Glad it works. As for marriage, let's just start out with a beer and see how things go.

inet is correct.

You might have a look in ethtool eth1 and man ethtool to see if something needs a tweak.

---

### Post by brooky on 2007-03-13
All sorted. I disabled the onboard by editing the BIOS and commented out its lines in the interfaces file. All fine and dandy now. Next thing it researching Samba performance. :)

Thanks again!

---

