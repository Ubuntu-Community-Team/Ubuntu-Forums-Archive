---
title: "Can't connect to internet"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by arturek on 2007-05-21
I looked at the other posts but no luck.....I'm running latest Xubuntu on HP DV6000 laptop.
From what I can tell the driver is working ("wireless light" is on), but I can't connect to the network.

After installing bcm43xx-fwcutter and typing in following two commands 
sudo bcm43xx-fwcutter -w /lib/firmware wl_apsta.o
and
sudo modprobe bcm43xx
wireless device turns on.  Using WiFi-Radar  I can see my network/access point , but when I try to connect to it I get a message that it "could not get IP address"
(I have no problem connecting to internet using wireless, from my desktop running latest Xubuntu)

output from iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"linksys"  Nickname:"linksys"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:10:E3:5F:47   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

output from ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:36:7D:81:1C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:C3:3E:2C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:159 errors:0 dropped:66 overruns:0 frame:0
          TX packets:1680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48119 (46.9 KiB)  TX bytes:72453 (70.7 KiB)
          Interrupt:255 

eth1:avah Link encap:Ethernet  HWaddr 00:14:A5:C3:3E:2C  
          inet addr:169.254.5.124  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:255 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18392 (17.9 KiB)  TX bytes:18392 (17.9 KiB)

output frow iwlist scan

 Cell 02 - Address: 00:13:10:E3:5F:47
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=85/100  Signal level=-71 dBm  Noise level=-69 dBm
                    Extra: Last beacon: 244ms ago

---

### Post by jglen490 on 2007-05-21
What does your /etc/network/interfaces file look like?  it may be a configuration problem.

---

### Post by arturek on 2007-05-22
/etc/network/interfaces

auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0
iface eth1 inet dhcp
wireless-essid linksys
wireless-key 1s41fg654v987h45s57e9ig444

I have no problem connecting to internet using wireless from my desktop .  I just can't figure out how to fix this, with help from all other similar posts.

---

### Post by blackdevil on 2007-05-22
having the same problem now too. My wireless was working before I restarted... now I'm having the same problem you are:(

---

