---
title: "WiFi at Home, No data"
date: 2017-02-23
forum: Networking &amp; Wireless
---

### Post by webmanoffesto on 2017-02-23
I'm on a laptop at home now. Yesterday I was at a cafe and used the WiFi there just fine. But at home it has been consistently not working. I have another laptop at home which uses the WiFi fine. I'm on Ethernet now.

I pasted the output of the Wireless Info script here. 
[http://paste.ubuntu.com/24054267/](http://paste.ubuntu.com/24054267/)

In it I see Wireless LAN is NOT blocked.

I see
FiOS-1PPJY           <MAC 'FiOS-1PPJY' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA2       yes     *
which I think says that I am connected (or can connect) to the correct WiFi access point
But in my browser I get no data via FireFox or Chromium

---

### Post by TheFu on 2017-02-23
Haven't looked at the data yet - thanks for that.

When websites don't open, that could be anything.  Start by determining where the issue lies. 
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has steps to take in order to determine where the issue lies. 

This could just be a DNS issue and have nothing to do with connectivity. Make sense?

**Updated**
Ok - looked over the data.
a) don't run a VPN. Disable that when troubleshooting.
b) don't have multiple networks enabled. Unplug the wired connections.  BTW, do you know why the wires and wifi subnets are different? Is that intended?

Something about ipv6 looks wrong. If you aren't using it, please disable it.

---

### Post by webmanoffesto on 2017-02-23
I unplugged the wired internet and disconnected the VPN and ran the Wireless Info script again
[http://pastebin.com/GYT8gykJ](http://pastebin.com/GYT8gykJ)

I don't know why [COLOR=#000000]the wires and wifi subnets are different.
[/COLOR]How do I disable ipv6?

---

### Post by TheFu on 2017-02-23
The data doesn't show what you claim. There are still VPN tunnels and the ethernet card is still enabled.
Did you run through the troubleshooting link with all the different pings too, as requested.

I'll await a complete, total response.

---

### Post by webmanoffesto on 2017-02-23
Output from the command line commands (with older Wireless Info below) which are on page [http://blog.jdpfu.com/2013/03/01/lin...101-networking]("http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking")[COLOR=#000000] [/COLOR]
[http://pastebin.com/RpbNiUdX](http://pastebin.com/RpbNiUdX)

---

### Post by TheFu on 2017-02-23
You need to use YOUR router's IP, not the one on that page, which was just an example.  Sorry if that wasn't clear, but it does say it in the page.

The VPN is still up. You'll need to fix that before doing anything else. Line 263 shows the routing table with tun0 interfaces. As long as any of those exist, the VPN is up and interfering.

The wired eithernet still has an IP and impacts the routing table.  As long as that is the situation, we cannot troubleshoot.

Lines 400-402 show the wifi subnet info. If your router isn't at the listed gateway IP, it won't work.

Basically, there are too many conflicting network settings to make troubleshooting 1 connection possible.

---

### Post by webmanoffesto on 2017-02-23
Ping'ing my router
```
tom@tom-HP-ProBook-450-G3:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.3.1 icmp_seq=1 Destination Net Unreachable
From 192.168.3.1 icmp_seq=2 Destination Net Unreachable
From 192.168.3.1 icmp_seq=3 Destination Net Unreachable
From 192.168.3.1 icmp_seq=4 Destination Net Unreachable
^C
--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, +4 errors, 100% packet loss, time 4005ms

tom@tom-HP-ProBook-450-G3:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.3.1 icmp_seq=1 Destination Net Unreachable
From 192.168.3.1 icmp_seq=2 Destination Net Unreachable
From 192.168.3.1 icmp_seq=3 Destination Net Unreachable
From 192.168.3.1 icmp_seq=4 Destination Net Unreachable
^C
--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, +4 errors, 100% packet loss, time 4005ms
```

I see
```
tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.61.10.6  netmask 255.255.255.255  destination 10.61.10.5
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 130479  bytes 159551653 (159.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 72239  bytes 6887398 (6.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
But how do I quit that / kill that process?

---

### Post by TheFu on 2017-02-24
I have no idea how you should stop the VPN running on your system. I didn't start it so it will depend on the controlling application. I'd search the system for any vpn software and remove it.

BTW, being disconnected from the wired ethernet may not be sufficient.  The settings used by that NIC need to be disabled as well.  On most systems, that would be automatic, but your system seems to have been setup very differently.

Gotta ask - why not get the person who setup all this stuff to help?

---

### Post by webmanoffesto on 2017-02-24
The person who set it all up is me. I'll reboot and see if the VPN is gone. I guess after reboot I'll see if "tun0" is running.

---

### Post by webmanoffesto on 2017-02-24
Okay, I ran Wireless Info Script
After Reboot and Without VPN Started
With Cabled Ethernet Internet disconnected
[https://hastebin.com/wagiloxole.coffeescript](https://hastebin.com/wagiloxole.coffeescript)

---

### Post by TheFu on 2017-02-24
Thanks for the info. All seems fine except the S/N varies wildly for the wifi network.

IP: 192.168.3.183
netmask 255.255.255.0
Gateway: 192.168.3.1
SSID: FiOS-1PPJY (however during the scan, the quality dropped to Quality=26/70!)
Connected at: 72.2 Mb/s
PwrMgnt: Off
Link quality is 100% 72/72
Signal Level: -32 dBm (excellent)

HW: RTL8188EE
[https://askubuntu.com/questions/786373/very-slow-wi-fi-on-intel-wireless-3165/786430#786430](https://askubuntu.com/questions/786373/very-slow-wi-fi-on-intel-wireless-3165/786430#786430) has some wifi settings to try. Chili is the guy (Wildman is too), though I wouldn't install firmware outside the package manager myself, I can see where someone who really had to have wifi might choose that rather than waiting a few months for the updates to work there way into the distro.  The main settings would be trying to stay with a specific AP and not let it switch too quickly looking for a stronger signal. If you aren't moving, that would be important.

Using "192.168.3.1" as the router IP, can you ping that over wifi from the client machine?  If so, what about 8.8.8.8?
If so, then the issue is probably DNS, not connectivity.

If no connectivity, try a newer driver or alternatively a newer kernel.  Kernels don't have to be tied to the release, but you'll be accepting the manual patching going forward. Let's avoid that, if we can.

So ... does the ping stuff work now or not? Where does it fail?

---

### Post by wildmanne39 on 2017-02-24
> though I wouldn't install firmware outside the package manager myself, I can see where someone who really had to have wifi might choose that rather than waiting a few months for the updates to work there way into the distro.
I have been working with wireless issues since 2011 and updated drivers or firmware do not always make it into the official repos in a timely manner, if you really want your device to work I would use the outside source if that is what is needed and with that driver I believe you it is but I could not read the whole script because the background color made it to difficult.

---

### Post by webmanoffesto on 2017-02-24
> **wildmanne39 said:**
>  I could not read the whole script because the background color made it to difficult.

When I attempted to update firmware I got an error
```
tom@tom-HP-ProBook-450-G3:~$ wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
--2017-02-24 22:27:06-- http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
Resolving mirrors.kernel.org (mirrors.kernel.org)... 198.145.20.143
Connecting to mirrors.kernel.org (mirrors.kernel.org)|198.145.20.143|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2017-02-24 22:27:06 ERROR 404: Not Found.
```

How do I install the correct update
Ubuntu – Details of package linux-firmware in yakkety-updates
[http://packages.ubuntu.com/yakkety-updates/linux-firmware](http://packages.ubuntu.com/yakkety-updates/linux-firmware)

```

tom@tom-HP-ProBook-450-G3:~$ sudo iw reg get
country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

```

I shut off IPV6 on the WiFi
Network / My WiFi Access Point / Settings for that Access Point / IPV6 set to "Off"


```

tom@tom-HP-ProBook-450-G3:~$ iwconfig
virbr0-nic  no wireless extensions.


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp3s0    IEEE 802.11  ESSID:"FiOS-1PPJY"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 48:5D:36:C3:96:60   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:20   Missed beacon:0


virbr0    no wireless extensions.


tom@tom-HP-ProBook-450-G3:~$ 


-----


tom@tom-HP-ProBook-450-G3:~$ ip add
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 98:e7:f4:5e:1f:3a brd ff:ff:ff:ff:ff:ff
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 54:8c:a0:05:d8:53 brd ff:ff:ff:ff:ff:ff
    inet 192.168.3.183/24 brd 192.168.3.255 scope global dynamic wlp3s0
       valid_lft 42051sec preferred_lft 42051sec
    inet6 fe80::56ae:8a31:3f07:6fc9/64 scope link 
       valid_lft forever preferred_lft forever
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
5: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 52:54:00:7d:80:d1 brd ff:ff:ff:ff:ff:ff
tom@tom-HP-ProBook-450-G3:~$ 


-----


tom@tom-HP-ProBook-450-G3:~$ ip route
default via 192.168.3.1 dev wlp3s0  proto static  metric 600 
169.254.0.0/16 dev virbr0  scope link  metric 1000 linkdown 
192.168.3.0/24 dev wlp3s0  proto kernel  scope link  src 192.168.3.183  metric 600 
192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1 linkdown 
tom@tom-HP-ProBook-450-G3:~$ 


-----


tom@tom-HP-ProBook-450-G3:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.3.1 icmp_seq=1 Destination Net Unreachable
From 192.168.3.1 icmp_seq=2 Destination Net Unreachable
From 192.168.3.1 icmp_seq=3 Destination Net Unreachable
From 192.168.3.1 icmp_seq=4 Destination Net Unreachable
^C
--- 8.8.8.8 ping statistics ---
6 packets transmitted, 0 received, +4 errors, 100% packet loss, time 5022ms


-----


tom@tom-HP-ProBook-450-G3:~$ ping google.com
ping: google.com: Name or service not known


-----


tom@tom-HP-ProBook-450-G3:~$ grep "name" /etc/resolv.conf
nameserver 127.0.1.1


-----






================
Friday 2017.02.24, 11:03
Ran Wireless Info Script
After Reboot and Without VPN Started
With Cabled Ethernet Internet disconnected
https://hastebin.com/lijutapapi.coffeescript


000000
0000


########## wireless info START ##########


Report from: 24 Feb 2017 10:58 EST -0500


Booted last: 24 Feb 2017 00:00 EST -0500


Script from: 30 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety


##### kernel ############################


Linux 4.8.0-39-generic #42-Ubuntu SMP Mon Feb 20 11:47:27 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8101]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company RTL8188EE Wireless Network Adapter [103c:804b]
    Kernel driver in use: rtl8188ee


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 04ca:7054 Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
rtl8188ee              86016  0
rtl_pci                28672  1 rtl8188ee
rtlwifi                77824  2 rtl_pci,rtl8188ee
mac80211              757760  3 rtl_pci,rtl8188ee,rtlwifi
cfg80211              581632  2 mac80211,rtlwifi
sparse_keymap          16384  3 intel_hid,intel_vbtn,hp_wmi
wmi                    16384  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 46512  bytes 31985396 (31.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 60690  bytes 70345367 (70.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 113495  bytes 7427559 (7.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 113495  bytes 7427559 (7.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


virbr0-nic: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.3.183  netmask 255.255.255.0  broadcast 192.168.3.255
        inet6 fe80::56ae:8a31:3f07:6fc9  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 5826  bytes 1334478 (1.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 565  bytes 67868 (67.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


virbr0-nic  no wireless extensions.


enp2s0    no wireless extensions.


lo        no wireless extensions.


virbr0    no wireless extensions.


wlp3s0    IEEE 802.11  ESSID:"FiOS-1PPJY"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'FiOS-1PPJY' [AN1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.3.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 virbr0
192.168.3.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0


##### resolv.conf #######################


nameserver 127.0.1.1
search lan


##### NetworkManager info ###############


GENERAL.DEVICE:                         virbr0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/1
GENERAL.IP-IFACE:                       virbr0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     virbr0
GENERAL.CON-UUID:                       212cb018-177b-4cef-95fd-3894b353597c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   212cb018-177b-4cef-95fd-3894b353597c | virbr0
IP4.ADDRESS[1]:                         192.168.122.1/24
IP4.GATEWAY:                            
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8188EE Wireless Network Adapter
GENERAL.DRIVER:                         rtl8188ee
GENERAL.DRIVER-VERSION:                 4.8.0-39-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FiOS-1PPJY
GENERAL.CON-UUID:                       5db5bd7c-acb0-4742-8191-0dae4d0a0eb3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   92be47ed-925c-48d0-a3b6-248e4b9b755b | FiOS-1PPJY 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   5db5bd7c-acb0-4742-8191-0dae4d0a0eb3 | FiOS-1PPJY
IP4.ADDRESS[1]:                         192.168.3.183/24
IP4.GATEWAY:                            192.168.3.1
IP4.DNS[1]:                             192.168.3.1
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.3.1
DHCP4.OPTION[5]:                        ip_address = 192.168.3.183
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.3.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.3.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 37800
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.3.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 21600
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = lan
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1487994807
DHCP4.OPTION[21]:                       host_name = tom-HP-ProBook-450-G3
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.3.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.3.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 43200
IP6.ADDRESS[1]:                         fe80::56ae:8a31:3f07:6fc9/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168h-2_0.0.2 02/26/15
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


GENERAL.DEVICE:                         virbr0-nic
GENERAL.TYPE:                           tun
GENERAL.NM-TYPE:                        NMDeviceTun
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         tun
GENERAL.DRIVER-VERSION:                 1.6
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/0
GENERAL.IP-IFACE:                       virbr0-nic
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            


SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
libreCMC-VPN         <MAC 'libreCMC-VPN' [AN9]>  Infra  11    2462 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
FiOS-1PPJY           <MAC 'FiOS-1PPJY' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 
ngHub_319436N8078D7  <MAC 'ngHub_319436N8078D7' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       no        
CV4NK                <MAC 'CV4NK' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       no        
KH677                <MAC 'KH677' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WEP        no        
Sampson WiFi         <MAC 'Sampson WiFi' [AN5]>  Infra  3     2422 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2       no        
xfinitywifi          <MAC 'xfinitywifi' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  50      &#9602;&#9604;__  --         no        
nyla                 <MAC 'nyla' [AN8]>  Infra  6     2437 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2  no        
ARRIS-C67A           <MAC 'ARRIS-C67A' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       no        
--                   <MAC '--' [AN10]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        
FiOS-1PPJY-vst02     <MAC 'FiOS-1PPJY-vst02' [AN11]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        
Belkin.5274          <MAC 'Belkin.5274' [AN12]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
6LXL3                <MAC '6LXL3' [AN13]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2       no        
xfinitywifi          <MAC 'xfinitywifi' [AN14]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  --         no        
NETGEAR81            <MAC 'NETGEAR81' [AN15]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
--                   <MAC '--' [AN16]>  Infra  3     2422 MHz  54 Mbit/s  27      &#9602;___  --         no        
xfinitywifi          <MAC 'xfinitywifi' [AN17]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  --         no        


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Artisan's Asylum]] (600 root)
[connection] id=Artisan's Asylum | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Artisan's Asylum
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FiOS-1PPJY]] (600 root)
[connection] id=FiOS-1PPJY | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FiOS-1PPJY
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FiOS-1PPJY 1]] (600 root)
[connection] id=FiOS-1PPJY 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FiOS-1PPJY
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Artisan's Asylum]] (600 root)
[connection] id=Artisan's Asylum | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Artisan's Asylum
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FiOS-1PPJY]] (600 root)
[connection] id=FiOS-1PPJY | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FiOS-1PPJY
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FiOS-1PPJY 1]] (600 root)
[connection] id=FiOS-1PPJY 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FiOS-1PPJY
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


virbr0-nic  no frequency information.


enp2s0    no frequency information.


lo        no frequency information.


virbr0    no frequency information.


wlp3s0    11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


Channel occupancy:


      6   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)


virbr0-nic  Interface doesn't support scanning.


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'FiOS-1PPJY' [AN1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"FiOS-1PPJY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000077eebc68bf
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Belkin.5274' [AN12]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Belkin.5274"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004017067a06
                    Extra: Last beacon: 164ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '6LXL3' [AN13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"6LXL3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009fbaeb180
                    Extra: Last beacon: 160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'FiOS-1PPJY-vst02' [AN11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"FiOS-1PPJY-vst02"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000077eeabf4d3
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'ngHub_319436N8078D7' [AN4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"ngHub_319436N8078D7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003e41b121293
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Sampson WiFi' [AN5]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Sampson WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006fbe520113
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'xfinitywifi' [AN6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e4718556cd
                    Extra: Last beacon: 32ms ago
          Cell 08 - Address: <MAC 'nyla' [AN8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"nyla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e471946180
                    Extra: Last beacon: 1172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '--' [AN10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e47195f224
                    Extra: Last beacon: 1148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'AKAY' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"AKAY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e471fda3b7
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'SBG6700AC-36798' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"SBG6700AC-36798"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ce80ab2df2
                    Extra: Last beacon: 572ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'KH677' [AN2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"KH677"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011b785c589
                    Extra: Last beacon: 32ms ago
          Cell 13 - Address: <MAC 'libreCMC-VPN' [AN9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"libreCMC-VPN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000476d761a4a2
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'CV4NK' [AN3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"CV4NK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f5245e1d9
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'ARRIS-C67A' [AN7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"ARRIS-C67A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ce4188393b
                    Extra: Last beacon: 444ms ago
               virbr0    Interface doesn't support scanning.


     IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8188ee]
filename:       /lib/modules/4.8.0-39-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     76177DA494B1AEFCCD3C2ED
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)


[rtl_pci]
filename:       /lib/modules/4.8.0-39-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     886A7942BD1E48BF21ECA79
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/4.8.0-39-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B936ED0E7D6B2CC6861A1AE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     9AF49B72127065FCF655D6A
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8188ee]
debug: 0
disable_watchdog: N
fwlps: N
ips: N
msi: Y
swenc: N
swlps: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################




grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################***


[   16.284023] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 3 times)
[   18.729896] wlp3s0: authenticate with <MAC 'FiOS-1PPJY' [AN1]>
[   18.749608] wlp3s0: send auth to <MAC 'FiOS-1PPJY' [AN1]> (try 1/3)
[   18.751147] wlp3s0: authenticated
[   18.753306] wlp3s0: associate with <MAC 'FiOS-1PPJY' [AN1]> (try 1/3)
[   18.757600] wlp3s0: RX AssocResp from <MAC 'FiOS-1PPJY' [AN1]> (capab=0x431 status=0 aid=1)
[   18.757870] wlp3s0: associated
[   18.757914] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[11461.093329] wlp3s0: deauthenticating from <MAC 'FiOS-1PPJY' [AN1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[11461.489076] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[11463.685647] wlp3s0: authenticate with <MAC 'FiOS-1PPJY' [AN1]>
[11463.705556] wlp3s0: send auth to <MAC 'FiOS-1PPJY' [AN1]> (try 1/3)
[11463.707511] wlp3s0: authenticated
[11463.708905] wlp3s0: associate with <MAC 'FiOS-1PPJY' [AN1]> (try 1/3)
[11463.712291] wlp3s0: RX AssocResp from <MAC 'FiOS-1PPJY' [AN1]> (capab=0x431 status=0 aid=1)
[11463.712595] wlp3s0: associated
[11463.712635] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[11479.017552] wlp3s0: deauthenticating from <MAC 'FiOS-1PPJY' [AN1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[11479.236261] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[11481.469516] wlp3s0: authenticate with <MAC 'FiOS-1PPJY' [AN1]>
[11481.489163] wlp3s0: send auth to <MAC 'FiOS-1PPJY' [AN1]> (try 1/3)
[11481.592782] wlp3s0: send auth to <MAC 'FiOS-1PPJY' [AN1]> (try 2/3)
[11481.696828] wlp3s0: send auth to <MAC 'FiOS-1PPJY' [AN1]> (try 3/3)
[11481.800817] wlp3s0: authentication with <MAC 'FiOS-1PPJY' [AN1]> timed out
[11488.805359] wlp3s0: authenticate with <MAC 'FiOS-1PPJY' [AN1]>
[11488.825073] wlp3s0: send auth to <MAC 'FiOS-1PPJY' [AN1]> (try 1/3)
[11488.826681] wlp3s0: authenticated
[11488.828906] wlp3s0: associate with <MAC 'FiOS-1PPJY' [AN1]> (try 1/3)
[11488.835615] wlp3s0: RX AssocResp from <MAC 'FiOS-1PPJY' [AN1]> (capab=0x431 status=0 aid=1)
[11488.835913] wlp3s0: associated
[11488.835957] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready


########## wireless info END ############
Page Saved!
 Archive Page
 Remove Page
 Open Pocket
 Settings
Add Tags


Want to find more great stories?
Explore Pocket's recommendations ›

```

---

### Post by TheFu on 2017-02-25
If you can't ping the GW/router, don't bother with anything else.
$ ping 192.168.3.1

---

