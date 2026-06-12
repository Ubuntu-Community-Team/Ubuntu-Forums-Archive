---
title: "need help configuring wireless usb adapter manually"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by tastybrains on 2008-03-11
Hello!

I need a little help getting my wireless USB device working.  I've set up ndiswrapper using the guides on this forum and had it working ok until i tried [setting my IP address manually]("http://ubuntuforums.org/showthread.php?t=684495"). now i can't connect at all! 

USB device: Netgear  WN121T
Driver: ndiswrapper + wb121t v5.1 (got superfast connection before)
using: WPA+ PSK, TKIP

Please let me know what settings, config files, logs you need me to post so i can fix this!

$route```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 wlan0
default         *               0.0.0.0         U     1000   0        0 wlan0
```
$iwconfig```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"squishy"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:2F:D5:FB:EA   
          Bit Rate=300 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
$sudo iwlist scan```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:D5:FB:EA
                    ESSID:"squishy"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

```
$ sudo lshw -C network```
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:2f:31:46:fe
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wn121t driverversion=1.52+Marvell,08/21/2007,1.0.6.7 link=yes multicast=yes wireless=IEEE 802.11g

```
$ sudo ifdown -v wlan0```
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
 route del default gw 10.0.0.1 metric 100 wlan0
SIOCDELRT: No such process 
```
$ sudo ifup -v wlan0```
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.wlan0.pid
Stopped /sbin/wpa_supplicant (pid 9389).
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...

```

anything else i need to post? 

thank you, 
tastybrains

---

### Post by kevdog on 2008-03-11
Yes
your wpa_supplicant.conf file
/etc/network/interfaces file

---

### Post by tastybrains on 2008-03-11
thanks for taking the time to reply, kevdog

/etc/networking/interfaces
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 10.0.0.202
gateway 10.0.0.1
dns-nameservers 10.0.0.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid squishy
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk de17e43e0f6497f99cdc567301223709e2e867d9b4b01c0fbcd6ac5751535ed3

```

/etc/wpa_supplicant.conf```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="squishy"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="myVeryLongConvolutedDefenseAgainstBruteForceAttacksPasswordExample"
        pairwise=TKIP
        group=TKIP
}
```

i converted my wpa-psk password for /etc/networking/interfaces [[COLOR="DarkOrange"]using this guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=318539") btw, and the one in supplicants is the original string as per the guides - hope that's right.

thanks again,
tastybrains

---

### Post by kevdog on 2008-03-12
Ok, since you are configuring your WPA setup via the interfaces file, you really dont need the wpa_supplicant.conf file since its basically duplicate info.

Your route statement contains no universal gateway.

When you say things are not working, what does that mean?

Can you ping the router?  Can you ping outside IP addresses by IP address rather than name?

Need more detail!

and 

ifconfig

---

### Post by tastybrains on 2008-03-12
What doesn't work is that i am not able to reach the gateway. so i can't reach the web either unfortunately. the ping command just keeps returning network unreachable.

I'm sorry i don't know what a universal gateway is - i searched the forums and google but didn't find it. what else would i need to add to /etc/network/interfaces?

more detail? no problem!

$ifconfig```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3275399 (3.1 MB)  TX bytes:3275399 (3.1 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1B:2F:31:46:FE  
          inet addr:10.0.0.202  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fe31:46fe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:52289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52281 errors:0 dropped:48165 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5908657 (5.6 MB)  TX bytes:7267059 (6.9 MB)
```
++++++++++++++++++++++++++++++++++++++
$ sudo ifdown wlan0
$ sudo ifup wlan0
tail -f /var/log/messages
```
Mar 12 19:44:58 zeus kernel: [89482.593547] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 12 19:45:02 zeus kernel: [89486.746901] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```
$ ping 10.0.0.1
```
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
From 10.0.0.202 icmp_seq=1 Destination Host Unreachable
From 10.0.0.202 icmp_seq=2 Destination Host Unreachable
From 10.0.0.202 icmp_seq=5 Destination Host Unreachable
From 10.0.0.202 icmp_seq=6 Destination Host Unreachable
```

$ route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 wlan0

```

$ ps -ef | grep [d]hclient
```
root      5893     1  0 Mar11 ?        00:00:00 /usr/sbin/dhcdbd --system
dhcp      9228     1  0 Mar11 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0

```

$ sudo ifconfig wlan0 down
$ tail -f /var/log/messages
```
Mar 12 20:13:54 zeus kernel: [91215.234584] ndiswrapper (NdisMSetInformationComplete:2544): invalid task
Mar 12 20:14:03 zeus kernel: [91224.485465] ndiswrapper (NdisMSetInformationComplete:2544): invalid task
Mar 12 20:14:17 zeus kernel: [91238.395753] ndiswrapper (NdisMSetInformationComplete:2544): invalid task
```

the interesting thing is my router show a device with MAC address: 00:1B:2F:31:46:FE, but 0.0.0.0 for the IP. so it evidently sees my computer! i've GOT to be close at this point

again, thanks for helping me, 
tastybrains

---

### Post by tastybrains on 2008-03-12
update

i renamed /etc/wpa_supplicant.conf to .bak, i killed the network manager processes, dhclient process and clicked on the network-admin tool. left my SSID selection on my router, chose WPA-Personal, left key as entered. then i choose DHCP. an voila! i got a connection. 

this is great, but unfortunately i don't know what i did to make this work right. 

well i'm going to post what the network-admin tool changed my /etc/network/interface file to:
```
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wpa-psk 03abcfb95290e089b707ce4fa6fcffc53d2bf80597afa61d3c8ab0f51482e909
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid squishy

```

my syslog shows:
```
Mar 12 22:14:45 zeus kernel: [ 6930.974638] ndiswrapper (NdisMIndicateStatus:2102): unrecognized PMKID ignored
Mar 12 22:19:40 zeus kernel: [ 7225.596865] ndiswrapper (NdisMIndicateStatus:2102): unrecognized PMKID ignored
Mar 12 22:24:50 zeus kernel: [ 7535.027867] ndiswrapper (NdisMIndicateStatus:2102): unrecognized PMKID ignored
Mar 12 22:40:59 zeus -- MARK --
Mar 12 23:00:59 zeus -- MARK --

```

i don't know what "unrecognized PMKID ignored" means in the syslog, i'll post more info if when i reboot i lose my connection again ;)

thanks kevdog for your assistance, 
tastybrains

---

