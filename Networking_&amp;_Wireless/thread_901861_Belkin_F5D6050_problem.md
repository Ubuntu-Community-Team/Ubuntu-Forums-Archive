---
title: "Belkin F5D6050 problem"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by Pixtu on 2008-08-26
I appear to be having a problem with the above USB wireless adapter.

It did work under 7.04 to begin with, then stopped.

I have now re-installed with 8.04 and I am experiencing the same problem, which is that I appear to have a connection but it indicates a signal strength of 0% and doesn't provide the IP address that it should. The same adapter in the same location works with Windows with near 100% strength.

The output from the various network commands is as follows:
lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0d5c:a002 Belkin F5D6050 802.11b Adapter
Bus 001 Device 001: ID 0000:0000  

lshw
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:30:bd:63:41:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=8.101.5-84 wireless=IEEE 802.11b

lsmod
at76_usb              108644  0 
usbcore               146028  3 at76_usb,uhci_hcd

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:190336 (185.8 KB)  TX bytes:190336 (185.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:30:bd:63:41:50  
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37875 (36.9 KB)  TX bytes:1264 (1.2 KB)

iwconfig
lo        no wireless extensions

wlan0     IEEE 802.11b  ESSID:wnet  Nickname:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

/etc/network/interfaces
auto lo
iface lo inet loopback

iwlist
wlan0     Scan completed :
          Cell 01 - Address: 00:18:F6:79:FE:07
                    ESSID:"BTHomeHub-CBBA"
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Quality:0  Signal level:0  Noise level:0
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1B:2F:A1:89:16
                    ESSID:"wnet"
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Signal level=16/100  
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

If I understand the output correctly, it would appear that the driver is working (at least to some degree) and that it can see our network (wnet).

We are using WEP security and the Network Manager does ask for the security key to be entered.

The only obvious thing that I can see that might be the issue is the lack of any mention in the 'interfaces' file. As this is a 'standard' Ubuntu install, should this not be entered by the system, rather than me having to enter it manually?

I have tried looking around the forum and have gone through the various HowTos.

I haven't yet tried using ndiswrapper but really want to avoid this if at all possible.

Any ideas?

Rgs,

---

### Post by Pixtu on 2008-10-24
As I still haven't been able to resolve this issue and have had no suggestions (I guess it slipped through the 'unanswered net') I'm bumping this msg because I really want to get connected. Without it, I can't update or download anything unless I keep switching back to Windows!

---

