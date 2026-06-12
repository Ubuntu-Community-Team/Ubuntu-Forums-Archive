---
title: "wireless -card ok -ubuntu not working"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by strider22 on 2008-08-11
My wireless has stopped working.

There are 3 laptops in the house that use the same wireless router.
This laptop dual boots to vista. Vista works. Ubuntu does not.
I don't have any thought as to why it may have stopped working.

wifi-radar asks for super password & then disappears without saying anything. I would expect a "Sorry You have no wireless" message or something.

There is no indication of why the wireless is not working. I would like to see.
1) cannot find your wireless interface.
2) cannot communicate with your interface
3) broadcasting with no reply -cannot find any router
4) router refused connection
5) ESSID/password bad
6) could not get DHCP  etc. etc.
You know stuff that lets me know what is happening.

Since I didn't know if the password was correct on the router: to make sure I changed it. The other 2 laptops and this one when booted to vista all work with the new password. 

I am writing this with the wired connection on.

Laptop is Toshiba P200-RT2

Below are the hints from the system per [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

> 
 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:48:96:1b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:fc:b1:07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.112 latency=0 module=r8169 multicast=yes


> 
chris@beryllium:~$ sudo ifconfig eth0 down
chris@beryllium:~$ sudo ifconfig wlan0 down
chris@beryllium:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:77:48:96:1b
Sending on   LPF/wlan0/00:1b:77:48:96:1b
Sending on   Socket/fallback


Any suggestions?

---

### Post by chili555 on 2008-08-11
> chris@beryllium:~$ sudo ifconfig eth0 down
chris@beryllium:~$ sudo ifconfig wlan0 down
chris@beryllium:~$ sudo dhclient -r wlan0All this seems to do is just stop everything. Please try this:```
sudo ifconfig eth0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <your_essid>
sudo iwconfig wlan0 key <any_encryption_here?>
sudo dhclient wlan0
```What is the result?

---

### Post by strider22 on 2008-08-12
Re sudo ifconfig wlan0 essid <your_essid>
I could not tell if essid is a keyword or my essid so I did both.
both report host not found. (same with or without quotes)
> chris@beryllium:~$ sudo ifconfig wmaster0 "mendeleev"
mendeleev: Unknown host
ifconfig: `--help' gives usage information.
chris@beryllium:~$ sudo ifconfig wmaster0 essid "mendeleev"
essid: Unknown host

leaving this mistake in for others... It should be iWconfig not iFconfig.


re dhclient:
The -r flag explicitly releases the current lease, and once  the  lease
has been released, the client exits.

The lshw -C network is supposed to give me my logical name but it showed wmaster0 which does not seem right.

re dhclient:
The -r flag explicitly releases the current lease, and once  the  lease
has been released, the client exits.

Note that dhclient does not show a mac address for wmaster0.

So is wmaster0 really the interface name? *****************

> 
chris@beryllium:~$ sudo dhclient -r
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/wlan0/00:1b:77:48:96:1b
Sending on   LPF/wlan0/00:1b:77:48:96:1b
Listening on LPF/eth0/00:16:d4:fc:b1:07
Sending on   LPF/eth0/00:16:d4:fc:b1:07
Sending on   Socket/fallback


preceeding the above with sudo ifconfig wlan0 down does not change the dhclient report... it still shows a mac address.


back to iwconfig
> 
chris@beryllium:~$ sudo iwconfig wlan0  essid mendeleev
chris@beryllium:~$ sudo iwconfig wlan0  key s:mypassword
chris@beryllium:~$ sudo iwconfig wlan0  mode Managed
chris@beryllium:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:77:48:96:1b
Sending on   LPF/wlan0/00:1b:77:48:96:1b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

same results with using "key open" after giving the key and doing ifconfig down/up first.

By the way I just changed the essid name to remove the space and my daughter came in to check... she is back up and running on the router with the new essid name so we know the router is responding.

---

### Post by strider22 on 2008-08-12
p.s. occasionally one of Network settings (via system admin) or wireless networks (via the network icon -edit wireless settings) will show the essid and the strength 73%.

---

### Post by strider22 on 2008-08-12
uncool. I used the graphic interfaces and changed the mode to roaming and this time it worked. (you can bet I've done that over and over for the past few days.)

thanks for the assistance chili

---

