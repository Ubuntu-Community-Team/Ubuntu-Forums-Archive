---
title: "Wifi Intel 2100 installation problem"
date: 2005-04-11
forum: Networking &amp; Wireless
---

### Post by FLo on 2005-04-11
Hello,

I've just switch to Ubuntu and it looks like a wonderful OS.
I just have a problem with my wifi connection. I'm using a Dell Inspiron 8600 with an Intel 2100 card. 
I can connect by ethernet but nothing happens by wifi. I've made a ndiswrapper install. I configure kwifi... what else should I do ? Is there some firmware or driver to install ? (I'm a newbie, so please be very explicit in your indication).

Thanks,
Flo

---

### Post by accuser on 2005-04-11
The Intel 2100 is based on the Broadcom chipset. I have a Linksys WMP54G that also has this chipset, and I had problems getting the thing working. Turns out the radio had been disabled by default when I installed the ndis driver. Please see [this](http://www.ubuntuforums.org/showpost.php?p=124727&postcount=4)  post for information about turning the radio on.

Enjoy!

---

### Post by alastair on 2005-04-11
Hold on - if you mean Intel 2100 "centrino"-style - this is the ipw2100 opensource driver and should be pretty much fully supported (I have one in my thinkpad).

Check your card using :

lspci -v

Also check the boot up messages in /var/log/syslog and see if any attempt is made to probe or load a driver for this Intel device.

---

### Post by FLo on 2005-04-12
[QUOTE=alastair]Hold on - if you mean Intel 2100 "centrino"-style - this is the ipw2100 opensource driver and should be pretty much fully supported (I have one in my thinkpad).[/QUOTE]

It's effectively a centrino.


[QUOTE=alastair]
Check your card using :
lspci -v[/QUOTE]

The result is :
0000:02:03.0 Network controller: Intel Corp. PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corp.: Unknown device 2561
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at faffc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

[QUOTE=alastair]
Also check the boot up messages in /var/log/syslog and see if any attempt is made to probe or load a driver for this Intel device.[/QUOTE]

The network seems to be detected but no connection available... :
Apr 12 09:06:06 localhost kernel: ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.0.2
Apr 12 09:06:06 localhost kernel: ipw2100: Copyright(c) 2003-2004 Intel Corporation
Apr 12 09:06:06 localhost kernel: ACPI: PCI interrupt 0000:02:03.0[A] -> GSI 5 (level, low) -> IRQ 5
Apr 12 09:06:06 localhost kernel: ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Apr 12 09:06:06 localhost kernel: b44: eth0: Link is down.


Thanks for your help,
Flo

---

### Post by alastair on 2005-04-12
Well, it looks like something is happening, so a device should be present.

What about :

iwconfig -a
ifconfig -a
route -n
cat /etc/network/interfaces

The first should show which device has wireless capability.

---

### Post by FLo on 2005-04-12
This is, the first have a problem... What should I do ?

* iwconfig -a
No such device


* ifconfig -a
eth0      Lien encap:Ethernet  HWaddr 00:0F:1F:0B:AC:92
          inet adr:192.168.0.101  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::20f:1fff:fe0b:ac92/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:0 (0.0 b)  TX bytes:398 (398.0 b)
          Interruption:11

eth1      Lien encap:Ethernet  HWaddr 00:0C:F1:18:DC:02
          inet adr:192.168.0.102  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::20c:f1ff:fe18:dc02/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 lg file transmission:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interruption:5 Adresse de base:0x4000 MÃ©moire:faffc000-faffcfff

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:HÃ´te
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Lien encap:IPv6-dans-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



* route -n

Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1




* cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.0.101
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 212.27.39.134

iface eth1 inet static
address 192.168.0.102
netmask 255.255.255.0

auto eth1

auto eth0

---

### Post by alastair on 2005-04-12
Many apologies - I have been silly and added a "-a" to "iwconfig" - try :

iwconfig

on its own.

I assume you will see "eth1" as being wireless. You are assigning a static address to it in the interfaces file (it is "UP" and ready).

Maybe you just need to specify the ESSID etc.?

---

### Post by FLo on 2005-04-13
Don't worry, I'm learning.
The result is pretty different : it seems the ESSID is wrong. I had configure it but now kwifi doesn't work anymore ! I can't use the administrator login... Is there a Konsole way to do the same thing ?

Thanks,
Flo

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power:off
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by alastair on 2005-04-13
I tend not to use the GUI - but the GUI's all run the command line equivalents anyway I think.

The think to do is play with the iwconfig program and various settings. You'll need to consider what your ESSID is, perhaps your access point (ap) MAC/HW address is, any WEP key etc.

e.g. try :

iwconfig eth1 ap <AP MAC address>
iwconfig eth1 key restricted <wep key>

or perhaps :

iwconfig eth1 essid "<ESSID>"

and check using "iwconfig" again.

If interfaces come up, you'll also need to think about routing perhaps i.e.

route -n

---

