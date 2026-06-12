---
title: "network card changes from eth2 to eth1"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by matt91 on 2007-06-28
i had an onboard network card which wasnt working with ethernet (although it was supposed to) so i got a pci gigabit card which i got working on eth1 fine (the onboard was on eth0). After a restart the network wasnt working so i plugged the network cable into the onboard and it then works (but not at gigabit speeds). The network cards keep swapping after each restart and i keep on having to switch network cables. How can i force the network card to stay on eth2? here is my network file where eth1 should be onboard and eth2 should be the pci one:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.11
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        dns-nameservers 62.6.40.178 194.72.0.98 192.168.1.254

auto eth2
iface eth2 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        dns-nameservers 62.6.40.178 194.72.0.98 192.168.1.254


---

### Post by crashovaride on 2007-06-28
You can do an ifconfig and see which cards you have. In /etc/iftab modify the file to the following:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac MAC:ADDRESS:HERE arp 1
ech1 mac MAC:ADDRESS:HERE arp 1

if you are having problems getting the device mac's you can do ifconfig eth# and it will be displayed as follows:

eth1      Link encap:Ethernet  HWaddr **THIS IS THE MAC ADDRESS**  
          inet6 addr: fe80::218:deff:fec1:f934/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13370 errors:0 dropped:2274 overruns:0 frame:0
          TX packets:13858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13190925 (12.5 MiB)  TX bytes:2379980 (2.2 MiB)
          Interrupt:17 Base address:0x6000 Memory:efcff000-efcfffff 

on my older machine, i completely commented out the eth0/eth1 and they stayed the same. Let me know if you need further help.

---

### Post by matt91 on 2007-06-28
Thanks, that worked, 2 restarts and they have stayed the same:D

---

### Post by crashovaride on 2007-06-28
ya mon, no worries. Best of luck.

---

### Post by matt91 on 2007-07-02
This has just happened again today so i have had to reconnect the ethernet cable to the other port and restart the networking which made it work, but this is likely to happen most times the server is switched on. here are some of my configs;

/etc/network/interfaces :
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.11
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        dns-nameservers 62.6.40.178 194.72.0.98 192.168.1.254

auto eth1
iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        dns-nameservers 62.6.40.178 194.72.0.98 192.168.1.254

ifconfig:
> root@server:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:17:5A:E1:F6
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe5a:e1f6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26695 (26.0 KiB)  TX bytes:2265 (2.2 KiB)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 00:0C:76:B3:8F:34
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:feb3:8f34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1677668 (1.5 MiB)  TX bytes:2771753 (2.6 MiB)
          Interrupt:17 Base address:0x6f00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9702 (9.4 KiB)  TX bytes:9702 (9.4 KiB)

/etc/iftab:
> # This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:12:17:5A:E1:F6 arp 1
eth1 mac 00:0C:76:B3:8F:34 arp 1

i dont know what is wrong, these all seem to be  correct with no typo's.:(

any ideas, Thanks.

---

### Post by matt91 on 2007-07-03
*bump*

---

### Post by crashovaride on 2007-07-03
I wish i had a solution for you at this point. However, i'm sorry to report that i don't.

---

### Post by coke on 2007-07-03
The common denominator here is that as soon as you installed the other ethernet card, your first one started working. This leads me to believe the chipset on both cards are either identical or near identical, and the system is confusing which adapter gets loaded first due to the chipset. This is theory however.

Sounds to me like that may be the issue.

---

### Post by matt91 on 2007-07-04
The onbourd one uses a realtek chipset whereas the PCI one (Linksys EG1032) uses a Marvell chipset. Is there a way of "deactivating" the onbourd one? i dont think there is an option in the bios to do this.

---

### Post by netztier on 2007-07-04
> **matt91 said:**
> 

```

# The primary network interface
auto eth0
iface eth0 inet static
[COLOR="Red"]address 192.168.1.[/COLOR]11
netmask 255.255.255.0
[COLOR="Red"]network 192.168.1.0[/COLOR]
broadcast 192.168.1.255
gateway 192.168.1.254
dns-nameservers 62.6.40.178 194.72.0.98 192.168.1.254

auto eth1
iface eth1 inet static
[COLOR="Red"]address 192.168.1[/COLOR].1
netmask 255.255.255.0
[COLOR="Red"]network 192.168.1.0[/COLOR]
broadcast 192.168.1.255
gateway 192.168.1.254
dns-nameservers 62.6.40.178 194.72.0.98 192.168.1.254

```

i dont know what is wrong, these all seem to be  correct with no typo's.:(



Having two interfaces in the same subnet is (basically) a "no go thing" - gives you trouble all over. It can be done, but only makes sense for very special requirements and then needs special configuration. Problems arise like: 

[LIST]
[*]"which Interface am I going to pick to talk to the default gateway?" 
[*]"which of the two routes to network 0.0.0.0 is my default route, actually?"
[*]"which source MAC-address should I use?" 
[*]"Shall i alternate between interfaces, and round-robin the MAC-addresses?"
[/LIST]

If you want to aggregate two physical into a single logical one, use **bonding** instead, and configure IP address, subnet mask and gateway parameters on the **bond0** interfaces

best regards

Marc

---

### Post by matt91 on 2007-07-04
iv commented out the onbourd one in /etc/network/interfaces as i dont need it at all. il see how it goes.

---

### Post by Mrkluky on 2007-07-11
Hi everybody ! I need your help
I have a FS Amilo laptop with integrated ethernet(Realtek) and wireless(IPW2200+ndispwrapper) .
I'm experiencing exactly the same problem.
My /etc/network/interfaces looks real messed up:

[INDENT]luca@Amilone:~$ cat /etc/network/interfaces

iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth1 inet dhcp
wireless-essid 3Com                         #this is my network at office

auto eth2
iface eth2 inet dhcp
wireless-essid Alice-17526654           #this is my network at home
wireless-key s:*************

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf


iface eth0 inet dhcp



auto eth1

auto eth0

auto lo[/INDENT]

I also wrote /etc/iftab

[INDENT]luca@Amilone:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:13:CE:B9:57:97
eth1 mac 00:03:0D:3A:D7:01[/INDENT]


any ideas?
Can you route me to any good how to configure /etc/network/interfaces ?

---

