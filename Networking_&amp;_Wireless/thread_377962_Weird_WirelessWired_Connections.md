---
title: "Weird Wireless/Wired Connections"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by drefined on 2007-03-06
Hey!

I would like to start off by saying hi! Im new to the forums and would like some help in regards to my IPW3945ABG connection.

First things first,... I am able to connect to the internet using a wired connect, no problem. The problem is that my wireless connection will not connect at all. I am able to see the wireless connection; the connection is open and is restricted to only this MAC address. For some reason when I try this command "sudo dhclient eth1" (which is the wireless connection) it says that it is sleeping. :confused:

Here are some of my outputs

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"DPs"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:09:5B:72:59:E6   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=-25 dBm  Noise level=-26 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:52803   Missed beacon:0

sit0      no wireless extensions.

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:4D:64:2B  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe4d:642b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2460265 (2.3 MiB)  TX bytes:171212 (167.1 KiB)

eth1      Link encap:Ethernet  HWaddr 00:13:02:CF:19:4B  
          inet6 addr: fe80::213:2ff:fecf:194b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16565 errors:0 dropped:52856 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3021 (2.9 KiB)  TX bytes:493989 (482.4 KiB)
          Interrupt:185 Base address:0x6000 Memory:da000000-da000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

```

iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:09:5B:72:59:E6
                    ESSID:"DPs"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:2
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=99/100  Signal level=-24 dBm  Noise level=-24 dBm
                    Extra: Last beacon: 36ms ago

sit0      Interface doesn't support scanning.

```

sudo gedit /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid DPs

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

If someone could help troubleshoot this problem, it would be greatly appreciated! :popcorn:

---

### Post by chili555 on 2007-03-06
Please try the following:

sudo gedit /etc/network/interfaces to amend as follows:```
**auto eth1**
iface eth1 inet dhcp
wireless-essid DPs
```

Then sudo /etc/init.d/networking restart

Let us know.

---

### Post by drefined on 2007-03-06
added:
**auto eth1**

sudo /etc/init.d/networking restart
```

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 3496
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:a0:d1:4d:64:2b
Sending on   LPF/eth0/00:a0:d1:4d:64:2b
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 4786
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:02:cf:19:4b
Sending on   LPF/eth1/00:13:02:cf:19:4b
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:a0:d1:4d:64:2b
Sending on   LPF/eth0/00:a0:d1:4d:64:2b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.6 -- renewal in 98401 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:02:cf:19:4b
Sending on   LPF/eth1/00:13:02:cf:19:4b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```

---

### Post by drefined on 2007-03-06
bump! :KS

---

### Post by chili555 on 2007-03-06
Looks like eth0 connected and got an IP address, try again with the ethernet cable disconnected. I don't think that eth0 (ethernet) and eth1 (wireless) will both connect with their own IP addresses.
```
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.6 -- renewal in 98401 seconds.
```

Let us know.

---

### Post by expat9 on 2007-03-06
I just today after a long time of trying figured out how to get my wireless connection to stay persistent after a reboot with wireless/WPA. 

Here is what I did to get my wireless networking working with WPA:

1. apt-get install wpasupplicant (you may already have wpasupplicant onboard)

2. sudo apt-get install network-manager-gnome network-manager

3. sudo nano /etc/network/interfaces
3a.  Comment out everything except the loopback interface info. Your interfaces file should like this:

auto lo
iface lo inet loopback

4. Create a file named /etc/default/wpasupplicant

sudo nano /etc/default/wpasupplicant

4. Add the following string in the file you just created:

ENABLED=0

Save the file.

5. Reboot

You should now have a network management icon up in the right-hand corner of your panel.

Select your wireless network and provide your credentials. Also supply a keyring password when requested. This needs to be different from your wireless access point or your Ubuntu login password for added security.

You should now be connected.

NOTES: I noticed that TKIP works great with my Netgear, but WPA-PSK2 with AES does not. Ubuntu may not support this encryption standard yet.

---

### Post by drefined on 2007-03-06
Ok, After disconnecting the cable, I tried renewing dhcp - it still says my wireless is still sleeping... I am sooooo stuck... :confused:

---

### Post by drefined on 2007-03-06
Added:
Gnome Network Manager...

It detects and communicates with the router but won't connect. Very odd, it works flawlessly with XP but doesn't want to cooperate with Ubuntu. My wired connection works but I want the ability to connect wirelessly incase I need to work in another area.. BAH!! /cry

---

### Post by chili555 on 2007-03-07
You said: > After disconnecting the cable, I tried renewing dhcp Did you do that with ifdown/up? Please try the following:
sudo ifdown eth0
sudo dhclient eth1

and then let us know the result. Thanks.

---

