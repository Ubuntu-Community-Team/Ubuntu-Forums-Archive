---
title: "Hardy Wireless Problem Intel 3945"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by SheridanLake on 2008-06-13
Dell Latitude D820.  Ubuntu Hardy 8.04.  Intel 3945 wireless won't connect.  I am new to Ubuntu.  I see wmaster0 is logical name displayed by "lshw -C network" but "iwconfig" shows wlan0 as connection.  Could this be possible problem I am having?  Thx in advance.  Details below:
dave@D820:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:37:ff:b8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.99 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:af:e1:07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5752-v3.19 ip=192.168.1.98 latency=0 module=tg3 multicast=yes
dave@D820:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:af:e1:07  
          inet addr:192.168.1.98  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feaf:e107/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1520885 (1.4 MB)  TX bytes:150926 (147.3 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:174300 (170.2 KB)  TX bytes:174300 (170.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:37:ff:b8  
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe37:ffb8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4501 (4.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-37-FF-B8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dave@D820:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Sheridan Park Resort"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:D1:34:77:3E   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=84/100  Signal level=-49 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dave@D820:~$

---

### Post by chili555 on 2008-06-13
I think your problem is Network Manager. [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)  Especially see this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managedAs long as you have an active connection wired, which you do, wireless is not going to activate.> eth0 Link encap:Ethernet HWaddr 00:15:c5:af:e1:07
inet addr:192.168.1.98 Bcast:192.168.1.255 Mask:255.255.255.0
   ...   ...   ...   snip   ...   ...   ...
RX bytes:1520885 (1.4 MB) TX bytes:150926 (147.3 KB)Please reboot with the wire detached and try again.

wmaster0 can safely be ignored.

---

### Post by SheridanLake on 2008-06-13
I have rebooted several times with Cat 5 disconnected. Can't even ping (other than the Intel 3945 itself).

---

### Post by chili555 on 2008-06-13
With the wire detached, please do:```
sudo iwconfig wlan0 essid "Sheridan Park Resort"
sudo iwconfig wlan0 key <any_encryption_here?>
sudo dhclient wlan0
```We would also like to see:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by SheridanLake on 2008-06-13
Below results with wire disconnected:
 sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:de:37:ff:b8
Sending on   LPF/wlan0/00:18:de:37:ff:b8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

dave@D820:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:D1:34:77:3E
                    ESSID:"Sheridan Park Resort"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=85/100  Signal level=-48 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000002bb4f637

---

### Post by chili555 on 2008-06-13
> Encryption key: onLooks like WEP is in place here. Did you input the key? Hex or ASCII? How many characters? Did you try both with and without *restricted*?```
sudo iwconfig wlan0 key 01234abcde **restricted**
```

---

### Post by SheridanLake on 2008-06-13
I relly appreciate your help.  More info:
Using WEP hex.  Working with Windows XP and Vista on same machine (I use a separate hard drive for Ubuntu).
Tried sudo iwconfig wlan0 key d820d1700d restricted (with & without restricted)
Tried installing hardy backports.
Tried wicd.
Have re-installed 3 times.
Still can't even ping router with wireless and wired disconnected..

---

### Post by hellododo on 2008-06-14
i'm having the same problem as you... please let me know when you can get your wireless to work.

---

### Post by chili555 on 2008-06-14
Let's see if we can rule out an issue with Network Manager by doing the connection process entirely manually.

Since your three re-installs, do you have hardy backports installed now? If not, please do. Detach the cable and please do:```
sudo iwconfig wlan0 essid "Sheridan Park Resort"
sudo iwconfig wlan0 key d820d1700d
sudo dhclient wlan0
```Do you connect or time out? I realize you have set up static IP addresses, but the quickest way to know if you have connected is if you do or do not get an IP address via DHCP.

May we see *cat /etc/network/interfaces*? Thanks.

---

### Post by SheridanLake on 2008-06-14
I will be off Ubuntu for next 2 days.  Will let you know if and when I resolve this issue.  In the meantime if you resolve the issue please post accordingly. Chili555 was trying to help.  Maybe try to contact him.

---

### Post by SheridanLake on 2008-06-24
Back to you Chilli555.  I did:
1) Clean install.
2) Nvida graphics driver install.
3) Install Ubuntu updates and rebooted.
4) Installed Hardy backports and rebooted.
5) Sequence below per your last response:

dave@D820:~$ sudo iwconfig wlan0 essid "Sheridan Park Resort"
[sudo] password for dave: 
dave@D820:~$ sudo iwconfig wlan0 essid "Sheridan Park Resort"
dave@D820:~$ sudo iwconfig wlan0 key d820d1700d
dave@D820:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:de:37:ff:b8
Sending on   LPF/wlan0/00:18:de:37:ff:b8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
dave@D820:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

===========  Thx in Advance Chilli555 ===========

---

### Post by chili555 on 2008-06-24
> dave@D820:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopbackSince *wlan0* is not listed, that tells Network Manager that it will control the interface. Just until we can reliable connect, let's *sudo gedit /etc/network/interfaces*. Any text editor will do, if you do not have gedit; use kwrite, kate, nano or vim. Amend it to add to the lo entries:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid "Sheridan Park Resort"
wireless-key d820d1700d

```Proofread, save and close the text editor. Now do:```
sudo ifdown wlan0 && sudo ifup wlan0
```Did you connect or time out?

---

### Post by SheridanLake on 2008-06-24
Did not connect.

---

### Post by SheridanLake on 2008-06-25
I tried NDISWRAPPER and then Wicd based on threads I read.  Nothing worked.  I then turned off the WEP security in Ubuntu and the router and bingo I am posting via wireless connection. One step forward!

Any suggestions as to why WEP won't work appreciated.

---

### Post by SheridanLake on 2008-06-25
Problem resolved.... Most routers can have up to 4 WEP keys stored. Any one of the 4 keys can be selected as the one to be used.  XP and Vista provide an index of 1-4 which points to the selected router key.  Ubuntu doesn't seem to support the index feature or I don't know how to use it.  In my case I had selected the 2nd key in the router and Ubuntu wasn't indexing to the 2nd key.

So I now have computers connected wirelessly to a router, which connects to an access point which connects wirelessly to a gateway about 850 feet away.

Special thanks to Chilli555 for his time and effort in assisting this Ubuntu newbie.

---

### Post by chili555 on 2008-06-25
If you want to index to the 2nd key, set *interfaces* like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid "Sheridan Park Resort"
wireless-key **[2]** d820d1700d
```

---

### Post by yfpjaya on 2008-07-04
I am having the same problem with intel 3945ABG driver for wireless. The output for 
#sudo dhclient wlan0 
has the last two lines as-
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Also, when I try to use the Network Manager to connect, the options WEP Hex and WEP ASCII do not seem to work. Any help is appreciated.

---

