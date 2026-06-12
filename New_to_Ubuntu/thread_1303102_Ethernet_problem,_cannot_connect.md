---
title: "Ethernet problem, cannot connect"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by 2uRcJQ34G1 on 2009-10-27
Hiya.

I am having trouble connecting to the internet. I am on my university lan(cisco). It was fine until this afternoon, when I plugged in my laptop at another lan in my university and when I brought it back to my residence. I could connect to the lan anymore. After searching some threads here are some things I did and their outcome:

ifconfig eth0:

eth0      Link encap:Ethernet  HWaddr 00:15:c5:ac:77:2f  
          inet addr:10.10.140.131  Bcast:10.10.140.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feac:772f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:418140 (418.1 KB)  TX bytes:4715 (4.7 KB)
          Interrupt:17 

Note: the TX bytes does not increase at all when I try to access a website.

sudo dhclient eth0:

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:15:c5:ac:77:2f
Sending on   LPF/eth0/00:15:c5:ac:77:2f
Sending on   Socket/fallback
DHCPREQUEST of 10.10.140.131 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.10.140.131 from 10.10.140.1
resolvconf: Error: /etc/resolv.conf must be a symlink
bound to 10.10.140.131 -- renewal in 268527 seconds.

ping google.com
ping: unknown host google.com

sudo ifconfig eth0 mtu 1000
sudo ifconfig eth0 mtu 1500
Note: neither worked

I have no idea what to do. Any ideas will be greatly appreciated.

Cheers.

---

### Post by 2uRcJQ34G1 on 2009-10-27
I forgot to mention:

I also tried to switch off (ifconfig ethO down and then up). Did not work.
This is annoying.

---

### Post by Buuntu on 2009-10-27
Is the connection showing up in network manager?  
This is probably a stupid question, but are you sure 'Enable Networking' is checked when you right click network manager?

---

### Post by pgar23 on 2009-10-27
> **gore_grinder said:**
> I forgot to mention:

I also tried to switch off (ifconfig ethO down and then up). Did not work.
This is annoying.
It is ```
ifconfig eth0 up
``` that is a ZERO not an "O". maybe try that..

---

### Post by pgar23 on 2009-10-27
> **Buuntu said:**
> Is the connection showing up in network manager?  
This is probably a stupid question, but are you sure 'Enable Networking' is checked when you right click network manager?
I second this. Right-click network manager and make sure that "Enable Networking" is checked. if it is, plug in your ethernet cable and try:
```
lshw -C network
```

---

### Post by 2uRcJQ34G1 on 2009-10-27
yes the enable networking is on. But the Auto Eht0 (not O as in orange) is no longer showing.

---

### Post by pgar23 on 2009-10-27
Try restarting your router and turning off everything for about 30 seconds. Then power back on, restart your computer and try again. That usually solves my networking issues when I use ethernet cable.

---

### Post by 2uRcJQ34G1 on 2009-10-27
"ifconfig eth0 up" yes i tried the same, it was just I am too frustrated to type the entire code. Moreover, lshw -C network gave me this output:

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:21:e8:95
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.103 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:ac:77:2f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.10.140.131 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:e8:e3:89:b0:98
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by pgar23 on 2009-10-27
Why not use wireless?

---

### Post by 2uRcJQ34G1 on 2009-10-27
i have restarted the computer and still no show. however, since i am dual booting with windows xp. XP is able to recognise the ethernet and i am able to log on to the internet with windows but not with ubuntu.

---

### Post by JBAlaska on 2009-10-27
> inet addr:10.10.140.131 Bcast:10.10.140.255 Mask:255.255.255.0

Me thinks DHCP Client error, try manually configuring a connection in Network Manager, Add a Local IP (Outside DHCP range), netmask, gateway addy and DNS servers.

Example:
```
IP:192.168.1.150 NetMask:255.255.255.0 Gateway: 192.168.1.1 And the DNS server Ip's of your school ISP
```

---

### Post by 2uRcJQ34G1 on 2009-10-27
i am presently using my friends wireless, but since our university caps the download at 350 kbps per user, we cannot share this. its too slow

---

### Post by pgar23 on 2009-10-27
> **gore_grinder said:**
> i have restarted the computer and still no show. however, since i am dual booting with windows xp. XP is able to recognise the ethernet and i am able to log on to the internet with windows but not with ubuntu.
No, you must restart router and everything else, and then your computer. It will reset configs and IP address for you. Hopefully you will establish a connection then.

---

### Post by 2uRcJQ34G1 on 2009-10-27
The university lan is through a CISCO phone. So i dont have a router.
10.10.140.131 and similar ips like this are our ip on the network. i have had such ips before thus this ip seems valid.

---

### Post by pgar23 on 2009-10-27
> **gore_grinder said:**
> The university lan is through a CISCO phone. So i dont have a router.
10.10.140.131 and similar ips like this are our ip on the network. i have had such ips before thus this ip seems valid.
So you should try to set up a manual connection. I think System > Admin > Network > Manual connection.

---

### Post by 2uRcJQ34G1 on 2009-10-27
however i did unplug  all the connections that i could get my hands on but still no show. something interesting though: after searching some more posts i found out something about resolv.conf since it says in my sudo dhclient error: resolvconf: Error: /etc/resolv.conf must be a symlink

thus i sudo gedit every resolvconf /resolv.conf file i could get my hands on and i wiped them clean in the hope of they will overwrite with fresh data. but nothing happend.

---

### Post by 2uRcJQ34G1 on 2009-10-27
i also typed network in the synaptic manager and reinstalled every network related file there is and then restarted my computer. and still nothing. i really appreciate you help mate ;)

---

### Post by 2uRcJQ34G1 on 2009-10-27
System > Admin > Network > Manual connection, i do not have this path however i can go to network connections and then manually add a wired network. in fact, i already did with all setting set to automatic, but still nothing

---

### Post by 2uRcJQ34G1 on 2009-10-27
is there anyway that i can reinstall resolvconf files, since these are linked with the DCHP and constantly refreshes the files whenever the wired network changes.

---

### Post by 2uRcJQ34G1 on 2009-10-27
i just tried to restart the network and this is my result:


 /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                                                                                                       ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
ifup: failed to open statefile /var/run/network/ifstate: Permission denied

---

### Post by 2uRcJQ34G1 on 2009-11-03
[FONT="Tahoma"][SIZE="6"][COLOR="Red"]I fixed it!!:guitar:[/COLOR][/SIZE][SIZE="4"]This is how:
if you see this error.
Error: /etc/resolv.conf must be a symlink

Here is the fix
$ cd /etc
$ sudo rm -rf /etc/resolv.conf
$/etc$ sudo ln -s /etc/resolvconf/run/resolv.conf

reboot the machine and try connecting again[/SIZE]
[SIZE="4"][COLOR="Blue"]Cheers to all those who tried to help.:KS[/COLOR][/SIZE][/FONT]

---

