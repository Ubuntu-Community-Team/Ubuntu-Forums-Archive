---
title: "[SOLVED] DWL-G630 &amp;quot;No DHCPoffers received&amp;quot;"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by nomis3613 on 2008-05-23
Hi,
I have previously been using wireless networking through NM but it drops out a lot so I want to try another method. I have followed the instructions in the [Manual Configuration]("http://ubuntuforums.org/showthread.php?t=684495") but I get an error when I try to configure the DHCP client and then it doesn't work in the final step. Can anyone please help? Or if someone can help me get it working in wicd, I'm happy to cheat and use a GUI.
Here's what happens when I follow the instructions:
```
general@simon-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:11:a1:5a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=10.1.1.2 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:17:9a:82:7e:14
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
```
Is my wireless device called wmaster0? I also have a device called wlan1.
```
general@simon-laptop:~$ sudo dhclient -r wmaster0
[sudo] password for general:
There is already a pid file /var/run/dhclient.pid with pid 23509
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
```
Everything else seems to go fine until I get to the final step:
```
general@simon-laptop:~$ sudo dhclient wmaster0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
Hmmmm...then no internet. Any help greatly appreciated.

---

### Post by chili555 on 2008-05-24
Your computer will not be at all happy with having two interfaces with two IP addresses. Since you are connected with your ethernet interface,> ip=10.1.1.2please detach the wire and do:```
sudo ifdown eth0
```wmaster0 is a phantom interface; why it's needed or what it does, I don't know. I do know it may be and, in my house, is ignored.

Please try:```
sudo iwconfig wlan1 essid <ur_essid>
sudo dhclient wlan1
```This assumes you have no encryption, WEP, WPA and the like.

Did you connect?

---

### Post by nomis3613 on 2008-05-24
Chilli,
Thanks for your help. Still no joy unfortunately. Please see below. My network is WEP encrypted by the way. Also, I noticed this in the instructions:
> sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
Do I need to specify open key? I think my router uses Open System Authenication. Any other ideas?

Thanks,
Simon

```
root@simon-laptop:/home/general# ifdown eth0
ifdown: interface eth0 not configured
root@simon-laptop:/home/general# iwconfig wlan1 essid WLAN
root@simon-laptop:/home/general# dhclient wlan1
There is already a pid file /var/run/dhclient.pid with pid 2343
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan1/00:17:9a:82:7e:14
Sending on   LPF/wlan1/00:17:9a:82:7e:14
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by chili555 on 2008-05-24
Some hairy ape wrote a decent post on WEP: [http://ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep](http://ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep)

The way to be sure you are using hex versus ascii is by key length. Valid key lengths are 5 (ASCII) and 10 (Hex) for 64-bit, 13 (ASCII) and 26 (Hex) for 128-bit WEP encryption. When you specify the key in *iwconfig,* if it is ascii, precede the key with **s:**

Post back if you get stuck.

---

### Post by nomis3613 on 2008-05-24
> **chili555 said:**
> Some hairy ape wrote a decent post on WEP: [http://ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep](http://ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep)

The way to be sure you are using hex versus ascii is by key length. Valid key lengths are 5 (ASCII) and 10 (Hex) for 64-bit, 13 (ASCII) and 26 (Hex) for 128-bit WEP encryption. When you specify the key in *iwconfig,* if it is ascii, precede the key with **s:**

Post back if you get stuck.

IT WORRRRRKKKKKKSSSSSSSSSSSS!!!!!!!!!!!!111111111111111!!!!!!!!!

Thankyou so much. I think the problem was the wired connection was not being killed by ifdown. I tried "ifconfig eth0 down" and then I was able to connect using Wicd. 

Now I'll just figure out how to get wicd into a startup script and it'll be perfect (another reason for doing this is I want to swap from xfce to dwm). Again, thanks.

---

