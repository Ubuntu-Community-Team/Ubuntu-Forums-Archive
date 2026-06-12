---
title: "Wireless confusion!"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by IanRats on 2007-11-20
I have reviewed the (many) threads on setting-up ndiswrapper and wireless but haven't found the answer to my issue, so here goes...

I have an old Tecra 8100 that I installed with Gutsy using the alternate cd.

After install, I installed ndiswrapper following the wiki to do so. **ndiswrapper -v** returns:

[FONT="Courier New"]utils version: 1.9
driver filename: /lib/modules/2.6.22.12-generic/ubuntu/misc/ndiswrapper/ndiswrapper/ndiswrapper.ko
version: 1.45
vermagic: 2.6.22-14-generic SMP mod_unload 586[/FONT]

I downloaded the older set of drivers for the Linksys wusb54g v4 card from [ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe](ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe) since I understood these to be more stable, extracted them in Windows and transferred them to the Tecra.

I then followed the instructions for installing the driver and if I now look at the list of installed drivers with **ndiswrapper -l** I see:

[FONT="Courier New"]rt2500usb : driver installed
             device (13B1:000D) present (alternate driver: rt2500usb)[/FONT]

I could connect to my open network (figured better to do this before encrypting) but the connection was very intermittent. If I pinged the router it would sometimes return and sometimes say **Network is unreachable**.

At this point, I noticed that I had neglected to add an entry to [FONT="Courier New"]/etc/modprobe.d/blacklist[/FONT] as described in [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419) to blacklist the Ralink drivers.

Thinking this was the issue, I added an entry [FONT="Courier New"]blacklist rt2500usb[/FONT] and rebooted.

Now I can't ever connect!

**ifconfig** returns:

[FONT="Courier New"]lo        Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:112 (112.0 b)  TX bytes:112 (112.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:18:39:05:3E:32
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6671 (6.5 KB)  TX bytes:7088 (6.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-39-05-3E-32-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/FONT]

**iwconfig** returns:

[FONT="Courier New"]wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/FONT]

Seeing that there was no Access Point associated, I did a Manual configuration and entered the correct Essid. I then ran **ifdown -a** followed by **ifup -a**, which returned the following:

[FONT="Courier New"]wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:39:05:3e:32
Sending on   LPF/wlan0/00:18:39:05:3e:32
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
Trying recorded lease 192.168.2.218
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.[/FONT]

I would appreciate any guidance to correct my amateur efforts and resolve this problem!

---

