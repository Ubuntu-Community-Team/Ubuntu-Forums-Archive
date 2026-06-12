---
title: "Networking (wired and wireless) stopped working Ubuntu 8.04 Hardy"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by rhimbo on 2008-06-25
Hi all,

Ubuntu 8.04 Hardy,.... DELL Inspiron 1150 laptop. 
Linksys router
Terayon cable modem.

Networking not working, neither wired or wireless from home.  

This was all working fine until Friday night when suddenly everything died. Now I don't even get the wireless icon in the top menu bar. 

Here are details. 

I cannot "ping" any host.

When I plug the laptop directly into the cable modem I get no IP address. When I plug it into the router I do get an IP address that is expected per Linksys (192.168.1.100). 

The tech support guy at Linksys says my networking must be fine if I am getting an IP address from the router. If this is true, it's the cable modem (or the Time-Warner network equipment) or my laptop. 

However, I think I still might have some problem with wireless. Today I went to a public Wi-Fi spot and my system did not even detect the presence of the wireless signal. I see no wireless signal bar icon in the menu bar either at home or in the public cafe. 

Unfortunately, I can't bring my laptop to work to see if wired works on another network 'cause they have everything on static IP addresses (Windows networking - and they won't give me one). 

Many thanks in advance. 

Here is some diagnostics data.

```

$ uname -a
Linux mandolin 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux
$ 
$ 
$ 
----------------------------------------------------------------
"ifconfig" output when laptop is connected directly to my cable modem.

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:1a:9e:2b  
          inet6 addr: fe80::20f:1fff:fe1a:9e2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36804 (35.9 KB)  TX bytes:5171 (5.0 KB)
          Interrupt:7 

eth1      Link encap:Ethernet  HWaddr 00:90:96:bb:32:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:fcffc000-fcffe000 

eth0:avahi Link encap:Ethernet  HWaddr 00:0f:1f:1a:9e:2b  
          inet addr:169.254.3.235  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:7 

eth1:avahi Link encap:Ethernet  HWaddr 00:90:96:bb:32:0a  
          inet addr:169.254.4.232  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Memory:fcffc000-fcffe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33797 (33.0 KB)  TX bytes:33797 (33.0 KB)

$ 

----------------------------------------------------------------------
"ifconfig" output when my laptop is connected to my router.

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:1a:9e:2b  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe1a:9e2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10141 (9.9 KB)  TX bytes:9119 (8.9 KB)
          Interrupt:7 

eth1      Link encap:Ethernet  HWaddr 00:90:96:bb:32:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:fcffc000-fcffe000 

eth1:avahi Link encap:Ethernet  HWaddr 00:90:96:bb:32:0a  
          inet addr:169.254.4.232  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Memory:fcffc000-fcffe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37553 (36.6 KB)  TX bytes:37553 (36.6 KB)

$ 
$ lspci -nv
00:00.0 0600: 8086:3580 (rev 02)
    Subsystem: 1028:017f
    Flags: bus master, fast devsel, latency 0
    Memory at <unassigned> (32-bit, prefetchable)
    Capabilities: <access denied>

00:00.1 0880: 8086:3584 (rev 02)
    Subsystem: 1028:017f
    Flags: bus master, fast devsel, latency 0

00:00.3 0880: 8086:3585 (rev 02)
    Subsystem: 1028:017f
    Flags: bus master, fast devsel, latency 0

00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA controller])
    Subsystem: 1028:017f
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at f6f80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at c000 [size=8]
    Capabilities: <access denied>

00:02.1 0380: 8086:3582 (rev 02)
    Subsystem: 1028:017f
    Flags: bus master, fast devsel, latency 0
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Memory at f6f00000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1d.0 0c03: 8086:24c2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: 1028:017f
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at bf80 [size=32]

00:1d.1 0c03: 8086:24c4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: 1028:017f
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at bf40 [size=32]

00:1d.2 0c03: 8086:24c7 (rev 01) (prog-if 00 [UHCI])
    Subsystem: 1028:017f
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at bf20 [size=32]

00:1d.7 0c03: 8086:24cd (rev 01) (prog-if 20 [EHCI])
    Subsystem: 1028:017f
    Flags: bus master, medium devsel, latency 0, IRQ 11
    Memory at f6effc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>

00:1e.0 0604: 8086:2448 (rev 81) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
    I/O behind bridge: 0000d000-0000efff
    Memory behind bridge: f8000000-fdffffff

00:1f.0 0601: 8086:24cc (rev 01)
    Flags: bus master, medium devsel, latency 0

00:1f.1 0101: 8086:24ca (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: 1028:017f
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at bfa0 [size=16]
    Memory at 50000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 0401: 8086:24c5 (rev 01)
    Subsystem: 1028:017f
    Flags: bus master, medium devsel, latency 0, IRQ 7
    I/O ports at c800 [size=256]
    I/O ports at cc40 [size=64]
    Memory at f6eff800 (32-bit, non-prefetchable) [size=512]
    Memory at f6eff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

00:1f.6 0703: 8086:24c6 (rev 01) (prog-if 00 [Generic])
    Subsystem: 14e4:4d64
    Flags: medium devsel, IRQ 7
    I/O ports at c400 [size=256]
    I/O ports at c080 [size=128]
    Capabilities: <access denied>

02:01.0 0200: 14e4:4401 (rev 01)
    Subsystem: 1028:017f
    Flags: bus master, fast devsel, latency 32, IRQ 7
    Memory at fcffe000 (32-bit, non-prefetchable) [size=8K]
    Expansion ROM at fc000000 [disabled] [size=16K]
    Capabilities: <access denied>

02:02.0 0280: 14e4:4320 (rev 03)
    Subsystem: 1028:0003
    Flags: bus master, fast devsel, latency 32, IRQ 11
    Memory at fcffc000 (32-bit, non-prefetchable) [size=8K]

02:04.0 0607: 104c:ac56
    Subsystem: 1028:017f
    Flags: bus master, medium devsel, latency 168, IRQ 11
    Memory at fc004000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: f8000000-fbfff000 (prefetchable)
    Memory window 1: 54000000-57fff000
    I/O window 0: 0000d000-0000d0ff
    I/O window 1: 0000d400-0000d4ff
    16-bit legacy interface ports at 0001

$ 
$
$ 
$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
$ 
$ 
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-key s:8187498609
wireless-essid feem

auto eth1

$ 
$


$ 

```

---

### Post by chili555 on 2008-06-25
As a temporary experiment, please edit /etc/network/interfaces to remove the s: and so it looks like:```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wireless-key 8187498609
wireless-essid feem
```Then restart networking:```
sudo /etc/init.d/networking restart
```Do you connect?

---

### Post by rhimbo on 2008-06-27
OK, folks, here is the requested information. I still can't get networking to work.

At first, I tried the suggested changes to /etc/network/interfaces. My file now looks like this:

```

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-key 8187498609
wireless-essid feem

auto eth1
$ 

```Then I restarted networking as suggested. Below is the command issued and standard output/error diagnostics:

```

~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 12816
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:90:96:bb:32:0a
Sending on   LPF/eth1/00:90:96:bb:32:0a
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:90:96:bb:32:0a
Sending on   LPF/eth1/00:90:96:bb:32:0a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
$  * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.
$
$

```So, now I can ping, and I can get to pages on the internet:

```

$ ping google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=242 time=84.5 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=242 time=81.7 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=242 time=84.9 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=4 ttl=242 time=81.3 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 81.332/83.142/84.937/1.626 ms
$ 

```But, wireless is not working. I set up wireless per the instructions on this page,
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c8cbba1734885284e4f79c2054461c863169f1bf](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c8cbba1734885284e4f79c2054461c863169f1bf)

My system seems to detect that my wireless router is present. But the signal shows 0% strength.

Now, if I click on the overlapping monitors and select my wireless network, the network monitor icon disappears from my menu bar. And my networking dies!! Now wired networking is hosed also! 

I cannot ping, browser or anything. Here is my system state thereafter (WITH my wired networking plugged into the laptop):

```

$ ping google.com
ping: unknown host google.com
$ 
$ 
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:1a:9e:2b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8617 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7922730 (7.5 MB)  TX bytes:1203615 (1.1 MB)
          Interrupt:7 

eth1      Link encap:Ethernet  HWaddr 00:90:96:bb:32:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:fcffc000-fcffe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70458 (68.8 KB)  TX bytes:70458 (68.8 KB)


$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
                                                                         [ OK ]
$ 

```I rebooted my system. After rebooting, the overlapping monitor icon appears once again in my menu bar. Clicking on it shows several wireless networks (the neighbors'). Mine does not appear.

"ifconfig" seems to indicate I have an IP address but I cannot ping or do any networking:

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:1a:9e:2b  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe1a:9e2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56079 (54.7 KB)  TX bytes:15648 (15.2 KB)
          Interrupt:7 

eth1      Link encap:Ethernet  HWaddr 00:90:96:bb:32:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:fcffc000-fcffe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41863 (40.8 KB)  TX bytes:41863 (40.8 KB)

$ ping google.com


```Nothing returns, just hangs.... Again I checked the state of my system:

```

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

$ 
$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

$ 
~$ lspci -n
00:00.0 0600: 8086:3580 (rev 02)
00:00.1 0880: 8086:3584 (rev 02)
00:00.3 0880: 8086:3585 (rev 02)
00:02.0 0300: 8086:3582 (rev 02)
00:02.1 0380: 8086:3582 (rev 02)
00:1d.0 0c03: 8086:24c2 (rev 01)
00:1d.1 0c03: 8086:24c4 (rev 01)
00:1d.2 0c03: 8086:24c7 (rev 01)
00:1d.7 0c03: 8086:24cd (rev 01)
00:1e.0 0604: 8086:2448 (rev 81)
00:1f.0 0601: 8086:24cc (rev 01)
00:1f.1 0101: 8086:24ca (rev 01)
00:1f.5 0401: 8086:24c5 (rev 01)
00:1f.6 0703: 8086:24c6 (rev 01)
02:01.0 0200: 14e4:4401 (rev 01)
02:02.0 0280: 14e4:4320 (rev 03)
02:04.0 0607: 104c:ac56
$ 

```
Any ideas? Again, many thanks in advance!

V

---

### Post by plewisfdx on 2008-06-27
It looks like originally you had network-manager disabled, and were connecting manually.  If /etc/network/interfaces configures eth1 network-manager will allow your "manual" settings to be used.

In a later post /etc/network/interfaces looks like all references to eth1 are removed, so network-manager is taking over.  

When you got an ip address and were able to ping it was on your wired connection, eth0, and was using that route to the internet.  It looks like when you restarted wireless at one point it tried to use eth1 as the internet route which wasn't configured, so you were not able to ping any servers.

It looks like wired is working ok, and if you can, you should pull the network cable out, restart networking, and double check your settings in network-manager, which appears to be running your wireless currently.  EDIT:see below, I don't think network-manager is running your wireless currently until you edit /etc/network/interfaces.

If you double check them, they are correct, and you still cannot login to your router, go to "System->Administration->Network" and click on "Properties" for eth1.  After applying these settings, eth1 will be restarted, this time manually (not using network-manager).

In your original post you said you couldn't see a wifi hotspot.  At that point you had eth1 configured manually by having eth1 info in /etc/network/interfaces.  Your wifi card was looking for essid "feem".  At one point your /etc/network/interfaces was only showing: 

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

If you return it to that state, and go to the wireless hotspot again, you should see the network in the network-manager applet at the top.  Then try to configure.  This would be a good test of your wifi on your computer and os.

If it works, then we're just looking at a home router setting.  I would turn off encryption on the router, and broadcast the essid, to make it as simple as possible.  Leave the /etc/network/interfaces file as I describe above, and see if network-manager will show you your network as an option.

---

### Post by rhimbo on 2008-06-27
Hi plewisfdx,

Thanks for your reply. Allow me to ask a few more questions for clarification. I'm going to try to understand precisely what to do so I can work on my system when I get back home. I'm posting this from the office 'cause I'm not sure I'll be able to from home if things are not working.  :-) 

Are you saying that I do need to configure eth1 in /etc/network/interfaces ? And, by doing so, wireless-manager will be able to detect my wireless? 

Do I configure eth1 via re-adding the following lines to /etc/network/interfaces ?

```

iface eth1 inet dhcp
wireless-key 8187498609
wireless-essid feem

auto eth1

```What is the gui for wireless-manager? Is it the same as the network manager? 
I don't understand what you mean by "wireless-manager" is taking over. 

Also, I don't understand why you said that wired networking is working OK. The last test I tried neither wired or wireless worked. 

I'm not sure I understand the difference between "manual" and "auto". I interpret "auto" to mean that everything gets configured on boot without me having to configure or "enable" via a gui. 

What is the difference between the wireless-manager applet and the network manager applet (is this the one with the overlapping monitor icons)? Are they really one and the same, but the icon that appears reflects whether the wired RJ-45 is plugged in or not? 

I can't find any wireless manager in any of my preferences or system administration menus. 

So, in sum, do I just add the above lines (at the top) to /etc/network/interfaces and restart my system? 

What else need I do? What do I need to do to automate this process on boot?

Many thanks again.  Cheers. 

V

---

### Post by Iowan on 2008-06-27
My interpretation (which has been known to be very wrong) is that the "managers" store their information in **/etc/network/interfaces**. Manually editing that file gets the information where it needs to be, but doesn't give the "managers" the opportunity to decide "what you REALLY wanted".

---

### Post by plewisfdx on 2008-06-27
> **rhimbo said:**
> 
Are you saying that I do need to configure eth1 in /etc/network/interfaces ? And, by doing so, wireless-manager will be able to detect my wireless? 

Sorry, replace all wireless-manager references to network-manager.  That was a mistake on my part.

But no, if you *manually *configure /etc/network/interfaces network-manager will not handle your wireless card.  The best place to manually configure it is "System->Administration->Network" which will populate /etc/network/interfaces for you.  

> **rhimbo said:**
> 
Do I configure eth1 via re-adding the following lines to /etc/network/interfaces ?

V

I apologize, I re-read my post, and even I was confused.

Here's what I'd do.  

1. You have eth1 config info already in /etc/network/interfaces currently, so lets start there.  This is the "manual" setting I was talking about.  
   - Unplug the ethernet cable (so we know when wireless is working), and open "System->Administration->Network".  
   - Select eth1 (your wireless) and click "Properties" on the right.  You should see your current settings there.  Make sure you have the essid and wep/wireless settings like you want, and make sure auto/dhcp is selected.  
   - When you click ok, see if the network settings are being applied (you'll see a dialogue come up telling you this).  If they aren't automatically applied, uncheck, then re-check eth1 (Your wireless card).
   - Open a terminal and ping 192.168.1.1 (your router).
   - Then paste the output of iwconfig and ifconfig if it doesn't work.

So thats manual, worth our first shot, since we're almost there right now anyway.

If that fails, then...

2. Network-manager

   - sudo gedit /etc/network/interfaces and make it look like this (removing all references to eth1)

```
auto lo
iface lo inet loopback
```
   - now click on the network manager in the top menu bar and see if you can see your network and re-enter your wep key there.
   - if you have problems, I would remove wep from your router and broadcast your ssid and see if you can connect to this "open" network
   - If not, I would return to the hotspot you talked about and see if you can see/join any networks
   - if this fails, post the output of this:
```
sudo ifup eth1
```
```
iwconfig
```
```
ifconfig
```
   - if all this fails, plug in your ethernet cable and 
```
sudo ifup eth0
```
```
ping 192.168.1.1
```
   - and at least your wired connection should work.

Sorry about the confusion and let me know how it goes.

I found this thread if you want to try more stuff also.
[http://ubuntuforums.org/showthread.php?t=667518](http://ubuntuforums.org/showthread.php?t=667518)

---

### Post by plewisfdx on 2008-06-27
> **Iowan said:**
> My interpretation (which has been known to be very wrong) is that the "managers" store their information in **/etc/network/interfaces**. Manually editing that file gets the information where it needs to be, but doesn't give the "managers" the opportunity to decide "what you REALLY wanted".

I don't think network-manager or wicd use /etc/network/interfaces, as my /etc/network/interface only has the lo interface and I have used both of those successfully with my wifi card.

This thread ([http://ubuntuforums.org/showthread.php?t=399632](http://ubuntuforums.org/showthread.php?t=399632)) says network-manager uses gconf and the gnome-keyring.  I can verify that network-manager uses the keyring!!!  It will remind you every login, sometimes twice!

---

### Post by rhimbo on 2008-06-30
OK, folks. Here is the status of my system. It's all messed up.... Neither wired or wireless is working now. I cannot get an IP address when plugged into my router nor when plugged directly into my cable modem.

My network applet cannot detect MY wireless router. However, when I left click on the double monitor icon, the drop down shows 8 wireless access points of my neighbors. 

I went to System->Administration->Network and reset the WIRED networking, both wired and wireless. I clicked "Properties" for wired and it gave me the "Configuring..." dialog with the progress bar each time (I did wired first, followed by wireless). 

I then did wireless. After configuring "Properties" my network applet could no longer detect my neighbors' wireless access points. Nor could it detect mine. 

I went back to reset wired networking to force it to reconfigure. Still could not get an IP address. I tried rebooting. I shut down, shut down my router, shut down my cable modem, and restarted in reverse order (cable modem, router, laptop). Still nothing.

Here is the output of the commands requested by plewisfdx.

```

$ sudo ifup eth0
ifup: interface eth0 already configured
$ 
$ sudo ifup eth1
ifup: interface eth1 already configured
$ 
$
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:1a:9e:2b  
          inet6 addr: fe80::20f:1fff:fe1a:9e2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37184 (36.3 KB)  TX bytes:19431 (18.9 KB)
          Interrupt:7 

eth1      Link encap:Ethernet  HWaddr 00:90:96:bb:32:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:fcffc000-fcffe000 

eth0:avahi Link encap:Ethernet  HWaddr 00:0f:1f:1a:9e:2b  
          inet addr:169.254.3.235  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:7 

eth1:avahi Link encap:Ethernet  HWaddr 00:90:96:bb:32:0a  
          inet addr:169.254.4.232  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Memory:fcffc000-fcffe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:751 errors:0 dropped:0 overruns:0 frame:0
          TX packets:751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39720 (38.7 KB)  TX bytes:39720 (38.7 KB)

$ 
$
$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

$ 
$ 
$ sudo ifup eth0
ifup: interface eth0 already configured
vartan@mandolin:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.3.235 icmp_seq=2 Destination Host Unreachable
From 169.254.3.235 icmp_seq=3 Destination Host Unreachable
From 169.254.3.235 icmp_seq=4 Destination Host Unreachable
From 169.254.3.235 icmp_seq=6 Destination Host Unreachable
From 169.254.3.235 icmp_seq=7 Destination Host Unreachable
From 169.254.3.235 icmp_seq=8 Destination Host Unreachable
From 169.254.3.235 icmp_seq=10 Destination Host Unreachable
From 169.254.3.235 icmp_seq=11 Destination Host Unreachable
From 169.254.3.235 icmp_seq=12 Destination Host Unreachable
From 169.254.3.235 icmp_seq=14 Destination Host Unreachable
From 169.254.3.235 icmp_seq=15 Destination Host Unreachable
From 169.254.3.235 icmp_seq=16 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
16 packets transmitted, 0 received, +12 errors, 100% packet loss, time 14999ms
, pipe 3
$ 

```
Thanks again everyone....

V

---

### Post by plewisfdx on 2008-07-01
> **rhimbo said:**
> I then did wireless. After configuring "Properties" my network applet could no longer detect my neighbors' wireless access points. Nor could it detect mine. 

I went back to reset wired networking to force it to reconfigure. Still could not get an IP address. I tried rebooting. I shut down, shut down my router, shut down my cable modem, and restarted in reverse order (cable modem, router, laptop). Still nothing.

Sorry it didn't work.

It looks like you tried suggestion 1 from my post, but not suggestion 2.    I'll re-post suggestion 2 below (with a slight change in italics).  

When you added the changes to the "manual" configuration of the networks it overrides network-manager, so thats why you aren't able to "see" your networks from the applet at the top of the screen.

[B]2. Network-manager
- *go to system->administration->network and click "properties" of the wireless, and check the box that says "enable roaming mode"*
- the above is easier than what I suggested first.

- now click on the network manager in the top menu bar and see if you can see your network and re-enter your wep key there.
- if you have problems, I would remove wep from your router and broadcast your ssid and see if you can connect to this "open" network
- If not, I would return to the hotspot you talked about and see if you can see/join any networks[/B]

---

### Post by rhimbo on 2008-07-01
Hi there,

Actually I did try your suggestion. Maybe I didn't explain clearly.

The problem is that I CANNOT remove WEP from my router because my wired networking is not working!! I can't even ping 192.168.1.1. I cannot ping anything. 

All networking is completely dead.

I'm thinking now that I need to reinstall. 

The problem cannot be hardware. If it was (at least for wireless) I would not be able to see my neighbors' wireless APs. As for wired, I can't say. I cannot get an IP address or ping anything regardless of whether I'm plugged into my router or directly into my cable modem.

Thanks all.

---

### Post by plewisfdx on 2008-07-01
Ok, but did you enable roaming mode to re-enable network-manager?

Network manager is not showing you any wireless networks because you have the manual settings (per my initial instructions) set.  

Unset these with "enable roaming mode" and then you should see all of your neighbor's wireless networks again, then take it to a coffee shop and see if you can join an "open" network.

---

### Post by rhimbo on 2008-07-02
Ah, sorry, I think I confused you. I guess my description left a lot to be desired.  :-)

I CAN see all of my neighbors' wireless networks already. They all show good signal strength. I can even "log in" to them. Well, not really, 'cause they're all password protected, but I get the prompt when I try to connect.

The problems I have are:

1. Wired networking does not work for me. I cannot ping anything, not even my router.
2. I cannot see my own wireless router. 


So, I am dead in the water with networking. 

IF one of my neighbors had an open access point, I would at least have wireless networking. 

Sorry I wasn't clear in my previous descriptions. (And I hope I'm understanding your comments correctly!!)

V

---

### Post by rhimbo on 2008-07-02
Sorry, I forgot to say....

Yes, I did click the check box for "Roaming mode". When I do, it grays out all the other options so I cannot set anything myself. 

In my previous post I was trying to say that this did not seem to affect anything. I still saw the same wireless APs (of my neighbors). I just can't connect because those APs are password protected. 

I tried selecting "Roaming mode" for my **wired** settings also. That didn't work either.

Thanks all.....

---

### Post by rhimbo on 2008-07-04
Hi all,

OK, I'm now writing this from the Panera Bread shop (which has a WiFi hot spot). I was able to connect immediately (wireless) doing what plewisfdx suggested (setting roaming mode). 

So this means my wireless hardware is definitely working. Furthermore, it means my OS configuration is correct for wireless. I get an IP address, I can ping internet sites, and I can browse.

HOWEVER, I am not able to test wired. Now I think I am going to call Linksys again and tell them it's NOT my computer. Hopefully they can debug whether my router is dead or whether it's my cable modem.

I thought that the router should serve up an IP address to the computer regardless of whether the cable modem is working (or whether the cable provider's network is working). Does anyone have any knowledge of this?

Thanks again to plewisfdx especially but all others who replied.

I'm still dead in the water at home so I hope I can get some answers from Linksys and Time-Warner (the worst service provider I've ever experienced).

V

---

### Post by mexpolk on 2008-07-04
My solution to this problem is **_[here]("http://ubuntuforums.org/showpost.php?p=5320732&postcount=18")_**.

---

### Post by rhimbo on 2008-07-04
OK, surprise. I'm at home posting the message. All is working, both wired and wireless.

After I came home from the cafe where I successfully connected to their wireless hot spot, I booted up and within a minute got an IP address wirelessly. I was able to ping arbitrary internet hosts, browse, etc. 

Then I confirmed that I could do the same wired.... very strange.

I wonder now if there was some state cached in my laptop that prohibited it from connecting to the router... did the router reject connection requests? Or, did the laptop state somehow prohibit DHCP from establishing a connection? I have no idea.

I called Linksys anyway. They recommended I flash new firmware. So I went to their web site and downloaded a new firmware file. I flashed it in the router. They tech support guy said that upgrade generally fixes several known problems. 

Anyway, the new firmware was not really the fix 'cause I regained network connectivity before flashing. I think somehow successfully connecting to the cafe's hot spot cleared some state in my laptop. Not sure where or what that would be.... Was it the ethernet and wireless hardware? I don't know. 

Anyway, it works now. 

Thanks all, especially plewisfdx for all your patience and help.

V

---

### Post by plewisfdx on 2008-07-05
Not sure what combination worked for you, but I'm glad its working!

That was brave reflashing AFTER successfully connecting.  I usually just don't touch anything! :)

---

