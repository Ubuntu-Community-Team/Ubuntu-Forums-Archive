---
title: "How to enable usb wireless adapter"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by Michele84 on 2006-11-12
Hi! First of all...I'm a new user of linux!! I'm not an expert..but I'd like to learn something!! So I install kubuntu 6.10..everything  works..exept my usb wireless adapter (USROBOTICS). Linux recognized the adapter, but I can't enable the adapter in the network administration: as root I try to enable but the green symbol (more or less the green V) does't remain and the red (X) returns!!!what can I do?
Please help me
PS:sorry for my bad english

---

### Post by FrodoB on 2006-11-12
You will have to publish some more information before anyone can say.  Please publish the outputs of:

lsusb


iwconfig


and the contents of the file: /etc/network/interfaces

Then someone may be able to assist you.

---

### Post by Bunbun on 2006-11-15
I got a similar problem, the USB device is there but just don't know how to enable it:

lsusb:
Bus 005 Device 009: ID 148f:2573 Ralink Technology, Corp.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 005: ID 04a9:1091 Canon, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

 cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

How can I enable this wireless adaptor?

---

### Post by FrodoB on 2006-11-15
Bunbun;

You seem to need the rt73 driver from what I can see on the web.  See my instruction for the Belkin F5D7050 ver 3000. You device is already in the source code, so it is even easier for your device.

Follow these instructions:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview)

It should work quite well.

---

### Post by Bunbun on 2006-11-17
Thanks for the info, it's realy helpful. I think i've got the interface up but still having trobule connecting the the wireless network. THe light on the USB adaptor oesn't flash at all. Here is the detail:

ifconfig:
rausb0    Link encap:Ethernet  HWaddr 00:14:78:74:59:C6
          inet6 addr: fe80::214:78ff:fe74:59c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:152851 (149.2 KiB)  TX bytes:7502 (7.3 KiB)

iwconfig
rausb0    RT73 WLAN  ESSID:"Harris_Wireless"
          Mode:Managed  Channel=6  Access Point: 00:11:95:9A:E5:70
          Bit Rate=18 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=63/100  Signal level:-76 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Using the wireless assistant it always said "conenction failed". I am sure I am using the correct key and WEP open authentication. 

Also this is the erros from wlassistant:
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
CONNECTION FAILED.

Any ideas?

---

### Post by Bunbun on 2006-11-17
Also if I do:

sudo ifdown rausb0

then 
sudo ifup rausb0

It will always crash the OS (e.g. everyhting just freeze and have to reboot PC)

---

### Post by FrodoB on 2006-11-17
When you see this:


iwconfig
rausb0 RT73 WLAN ESSID:"Harris_Wireless"
Mode:Managed Channel=6 Access Point: 00:11:95:9A:E5:70
Bit Rate=18 Mb/s
RTS thrff Fragment thrff
Link Quality=63/100 Signal level:-76 dBm Noise level:-115 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

The fact that the Access Point has the MAC identifier filled in tells you that you are connected.

What do you have in your /etc/network/interfaces file?
Also, what is the output of netstat -rn at this point?

---

### Post by Bunbun on 2006-11-19
The wireless card seem to have found some access point but failed to connect.

"ifconfig rausb0" doesn't show the IP that is assigned.

Here is the netstat -rn output:
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG        0 0          0 eth0


cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

# rt73 wireless network device using DHCP
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid Harris_Wireless
wireless-key s:mypassphrasehere
auto rausb0

Any more help?

thanks

---

### Post by FrodoB on 2006-11-19
> **Bunbun said:**
> The wireless card seem to have found some access point but failed to connect.

"ifconfig rausb0" doesn't show the IP that is assigned.

Here is the netstat -rn output:
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG        0 0          0 eth0


cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

# rt73 wireless network device using DHCP
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid Harris_Wireless
wireless-key s:mypassphrasehere
auto rausb0

Any more help?

thanks


Well, actually you appear to be connected to the router correctly, but the data so not seem likely to be correct, they may be.

Your default router is at 10.1.1.1 

Your genmask looks different, most folks would have 255.255.255.0 in the line above. Do you know that this is correct? Have you tried to ping 10.1.1.1 and if it works then [www.google.com](www.google.com) perhaps. Do you know that your router is logged into your account. Maybe you are hooked to the router, but the router is not on the internet?


Here is the netstat -rn output:
Destination Gateway     Genmask  Flags MSS Window irtt  Iface
10.0.0.0    0.0.0.0    255.0.0.0 U     0     0      0   eth0
0.0.0.0     10.1.1.1   0.0.0.0   UG    0     0      0   eth0

---

### Post by Bunbun on 2006-11-19
Yes I agree, netmask of 255.255.255.0 is more common although it works fine on the wired network adaptor eth0 with this settings so I use the same for the wireless interface rausb01. Pinging 10.1.1.1 and also outside world works fine on the wired connection eth0. 

As soon as I disable the eth0 and change the default route to rausb01 it stop working. 

I also tried setting the rausb01 to use a static IP of 10.1.1.5It assigned the IP to interface rausb01 ok but I can't ping anywhere, not even the 10.1.1.1. On the wireless router I check the status to see which LAN clients are connected but couldn't see the 10.1.1.5. I even enetered the MAC address of the usb adaptor and the IP of 10.1.1.5 into the wireless router but no luck. The usb adaptor is a working one as I tested it in Windowxs XP. The wireless-key is correct and it is using WEP Open authentication.

---

### Post by Bunbun on 2006-11-20
I assigned a static IP to the USB, I got it to a stage where it can only receive packets but not transmit. I can ping the IP 10.1.1.5 from my router but I can't ping the router 10.1.1.1 from my usb adaptor, really strange !

Here is output from ifconfig:
rausb0    Link encap:Ethernet  HWaddr 00:14:78:74:59:C6
          inet addr:10.1.1.5  Bcast:10.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::214:78ff:fe74:59c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16950 errors:0 dropped:0 overruns:0 frame:0
          TX packets:365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:[COLOR="Red"]1332314[/COLOR] (1.2 MiB)  TX bytes:[COLOR="Red"]22706[/COLOR] (22.1 KiB)

It keep receiving packets but just not transmitting much.


I did some more digging around and found someone else had a similar problem here: [http://ubuntuforums.org/archive/index.php/t-7501.html](http://ubuntuforums.org/archive/index.php/t-7501.html)

There is no firewall in my PC. Also I update the routing table to have this but still didn't work:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        0.0.0.0         255.255.255.0   U     0      0        0 rausb01
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 rausb01

Also dmesg had this:

[4295014.635000] usb 5-7: new high speed USB device using ehci_hcd and address 2[4295014.890000] idVendor = 0x148f, idProduct = 0x2573
[4295014.971000] rausb0 (WE) : Driver using old **/proc/net/wireless support, please fix driver !**
[4295014.984000] rt73 driver version - 1.0.3.6
[4295025.798000] rausb0: no IPv6 routers present
[4295158.429000] usb 5-7: USB disconnect, address 2
[4295158.429000] unregister_netdev()
[4295184.885000] usb 5-7: new high speed USB device using ehci_hcd and address 3[4295185.140000] idVendor = 0x148f, idProduct = 0x2573
[4295185.222000] rt73 driver version - 1.0.3.6
[4295196.113000] rausb0: no IPv6 routers present

---

### Post by FrodoB on 2006-11-20
Well, It seems that you probably need to go back to the settings that you had before. Use 255.0.0.0 as your netmask, as it sees to be what is in your router still from the message from netstat -rn. 

For purposes of debugging only, I would remove all encryption on the router  and comment it out in the interfaces file with a "#" character in the first position in front of the WEP key.

Are you using WEP on the access point or something else? If WEP is it 128bit(104bit) WEP?

If you are using WEP the keys can be problematic, see:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

For a good generator that can give you the keys in ASCII and HEX for the same value. After things are going I can say that some people seem to have better luck using HEX keys, at least on the Linux side.

You certainly seem to be very close. The only part that I have not seen with my device is the freezing. Are you sure that you do not have a competing driver that is still loading with this device? This sounds more like the behaviour that I see with devices that use the rt25XX series of drivers.

---

### Post by FrodoB on 2006-11-20
I found another issue, I had to fix my installion docs. 

Make sure that your blacklist contains these three lines at the end:

# Added when rt73 module was installed[FONT=monospace]
[/FONT]blacklist rt73usb[FONT=monospace]
[/FONT]blacklist rt2570

I tried my Belkin on a fairly clean install of Dapper and the rt2570 was comming on and acting strangely. Not freezing completly, but not allowing any new applications to be started.  This may have something to do with your issue. Reboot after fixing the blacklist and try again.

You can check for the rt2570 by running the lsmod command and paging through the results:

$ lsmod |more

Get rt73usb and rt2570 in the blacklist and reboot. Maybe we will have improvement.

---

### Post by Bunbun on 2006-11-21
Thanks for the info. I did tried the key gen page you suggested but no luck. So I removed the Security on the wireless AP and tried. Here is what I have:

from the router I can ping the IP 10.1.1.5:
PING 10.1.1.5 (10.1.1.5): 64 data bytes
72 bytes from 10.1.1.5: icmp_seq=0 ttl=64 time=0.0 ms
72 bytes from 10.1.1.5: icmp_seq=1 ttl=64 time=0.0 ms
72 bytes from 10.1.1.5: icmp_seq=2 ttl=64 time=0.0 ms
--- 10.1.1.5 ping statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 0.0/0.0/0.0 ms 

netstat -rn has this(I made all traffic in 10.1.1.0 to go through rausb0):
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.1.1.0        0.0.0.0         255.255.255.0   U         0 0          0 rausb0
0.0.0.0         10.1.1.1        0.0.0.0         UG        0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0

From the usb adaptor I cannot ping the router 10.1.1.1:
ping 10.1.1.1
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
From 10.1.1.5 icmp_seq=1 Destination Host Unreachable
From 10.1.1.5 icmp_seq=2 Destination Host Unreachable
From 10.1.1.5 icmp_seq=3 Destination Host Unreachable
From 10.1.1.5 icmp_seq=5 Destination Host Unreachable
From 10.1.1.5 icmp_seq=6 Destination Host Unreachable
From 10.1.1.5 icmp_seq=7 Destination Host Unreachable

ping yahoo.com is ok because it goes out via eth0
PING yahoo.com (216.109.112.135) 56(84) bytes of data.
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=1 ttl=50 time=257 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=2 ttl=50 time=257 ms

iwconfig:
rausb0    RT73 WLAN  ESSID:""
          Mode:Auto  Channel=6  Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:
rausb0    Link encap:Ethernet  HWaddr 00:14:78:74:59:C6
          inet addr:10.1.1.5  Bcast:10.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::214:78ff:fe74:59c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3853458 (3.6 MiB)  TX bytes:849784 (829.8 KiB)

---

### Post by FrodoB on 2006-11-21
Have you gone back and followed these instructions carefully:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview)

I do not believe that it will work otherwise.

---

### Post by Bunbun on 2006-11-21
Thanks FrodoB!

It's working now! I think the problem is with the KEY. I thought it was correct but I use the Hex key as an ascii key(my fault). I found out when I remove security on the wireless AP. I don't know why it wasn't working the first time without security. Then I rebooted my machine and it worked. So I examine the key more carefully and found out. 

One problem still remain is whenever I do a ifconfig rausb0 down/up it will always freeze my PC and had to reboot. yes I have blacklisted the two drivers you suggested and rebooted but no luck.

---

