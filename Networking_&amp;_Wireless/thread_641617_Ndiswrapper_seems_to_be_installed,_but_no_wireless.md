---
title: "Ndiswrapper seems to be installed, but no wireless"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by Omkar Lele on 2007-12-15
I installed the driver for my Atheros wireless card, here's the output for ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

It worked only once after installation, but never after a subsequent reboot.
I'm posting the output of some of the commands, I just cant seem to get it to work again.

omkar@omkar-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 wlan0

omkar@omkar-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


omkar@omkar-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:38:11:ED:CB  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe11:edcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1899857 (1.8 MB)  TX bytes:300542 (293.4 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4484 (4.3 KB)  TX bytes:4484 (4.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1B:9E:28:A3:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Memory:f8200000-f8210000 

wlan0:ava Link encap:Ethernet  HWaddr 00:1B:9E:28:A3:66  
          inet addr:169.254.6.90  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:f8200000-f8210000 


omkar@omkar-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
address 192.168.168.40
gateway 192.168.168.230
dns-nameservers 192.168.168.230
netmask 255.255.255.0
wpa-driver wext
wpa-ssid MashConCong
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <The hex key here>



iface eth0 inet dhcp

auto eth0


omkar@omkar-laptop:~$ cat /etc/modprobe.d/ndiswrapper 
alias wlan0 ndiswrapper


omkar@omkar-laptop:~$ cat /etc/resolv.conf
search columbus.rr.com
nameserver 65.24.7.3
nameserver 65.24.7.6

I dont know what I should do next. My laptop is Toshiba Satellite A215-S4807

---

### Post by gilf on 2007-12-15
Go back to square one.

Boot from your liveCD. In the liveCD session, click on the network icon in the upper right corner of your screen. If you then see some networks with bar graphs, **click a bargraph network line  that you want to connect to**. If you are then connected, see the following post:

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

