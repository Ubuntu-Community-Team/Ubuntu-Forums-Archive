---
title: "/network/interfaces for wireless"
date: 2005-10-04
forum: Networking &amp; Wireless
---

### Post by paxmark on 2005-10-04
Kubuntu

Was a bit of work, but got two different cards to work with Ubuntu on two different machines (ACX 802.11b's and a dlink 802.11g router)

Problem, they did not come up on their own.  I would have to go into Kwifimanager to configure.  And then I always had to sudo dhclinet wlan0

so - Have been rtfm ing especially on /network/interfaces

nice web site is [http://arstechnica.com/columns/linux/linux-20040413.ars/2](http://arstechnica.com/columns/linux/linux-20040413.ars/2)

AFter playing around with /network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

# The primary network interface
iface wlan0 inet dhcp
     wireless_ap 00:0D:88:89:CE:AF
#    wireless_ap 00:13:46:3E:B1:B2
     wireless_freq 2.437G
     wireless_channel 6
     wireless_mode managed
     # wireless_key1 0123456789
     # wireless_key2 0123456789
     # wireless_key3 0123456789
     #  wireless_key4 0123456789
     # wireless_keymode restricted

ifconfig follows

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0D:88:89:CE:AF
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fe89:ceaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2237 errors:36 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2313912 (2.2 MiB)  TX bytes:315639 (308.2 KiB)
          Interrupt:10 Base address:0xeca0

and iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"default"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:3E:B1:B2
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=176/255
          Retry min limit:7   RTS thr:off
          Encryption key:off
          Power Management:off
          Link Quality=53/100  Signal level=37/100  Noise level=1/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:36  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


It comes up on the correct frequency and channel, but I have to activate.

And then I have to sudo dhclient wlan0 still.  At one point I only had to sudo dhclient.

Questions

1.  on sit0 what is hardware 776  and why is it not recognized.  I see a lot of this in printout of problems, but never an answer.

2.  For wireless_ap do I want the ap # of the nic or the router  And 00:0D:88:89:CE:AF or ipv6

3.  On one machine Kubuntu configured the hotplug mapping coming before the auto stanzas, on the other the auto stanzas come first.  Which is preferable on machines that will only have a wifi nic and not ethernet card

I am guessing that on the one the initial set up was done with only a wifi nic, and on the other, the intial setup had a ethernet card.

Sorry to take up so much space and time.

---

