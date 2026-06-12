---
title: "No network connection after 16.0.4.2 LTS install"
date: 2017-05-27
forum: Networking &amp; Wireless
---

### Post by jared_m on 2017-05-27
I installed 16.0.4.2 LTS on my machine, and it is dual bootable with Windows 10.  After the installation, my ethernet network shows connected, but I can't get to the internet.  I did an ifconfig and dmesg and saw that I have no IPv4 address (the results are pasted below).  I tried Ignoring IPv6, and never got an IPv4 address.  Any help would be greatly appreciated!


```
:~$ ifconfig

eno1      Link encap:Ethernet  HWaddr e0:3f:49:ae:b9:7d  
          inet6 addr: fe80::964f:2f5f:353b:5971/64 Scope:Link
          inet6 addr: 2601:c3:8001:b980:a0bb:3fbe:b087:efa0/64 Scope:Global
          inet6 addr: 2601:c3:8001:b980:b61a:1804:be62:3b8e/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2980 (2.9 KB)  TX bytes:12385 (12.3 KB)
          Interrupt:20 Memory:f7200000-f7220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:42670 (42.6 KB)  TX bytes:42670 (42.6 KB)



:~$ dmesg | grep eth0
[    0.907922] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) e0:3f:49:ae:b9:7d
[    0.907923] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.907967] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    0.908314] e1000e 0000:00:19.0 eno1: renamed from eth0

:~$ dmesg | grep eno1
[    0.908314] e1000e 0000:00:19.0 eno1: renamed from eth0
[   19.228505] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   19.415155] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   22.324850] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   22.324877] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
```

---

### Post by ubfan1 on 2017-05-27
Is your router set up to assign (dhcp) IPV4 addresses?  What address range is it assigning, and how many are allowed?  Looks like the IPv6 is not being ignored.

---

### Post by jared_m on 2017-05-27
Yes, my router is set up to assign dhcp addresses beginning at 10.0.0.2 through 10.0.0.252.  I don't see any setting for the number allowed.

---

### Post by ubfan1 on 2017-05-28
How were you trying to ignore IPv6?  Under the network manager icon in the title bar, there is an "edit connections" menu choice, under that, an IPV6 tab, and set the drop down to ignore.
When ignored, you don't get the ipv6 messages in dmesg output.  Then you might get an ipv4 address.  Also, does the router give you a preference on assigning ipv4 over ipv6?  Maybe disallow ipv6 threre too.

---

### Post by jared_m on 2017-05-29
I tried to ignore IPv6 under the Network Manager.  I think I have a workable solution now.  In Windows10, I logged into my router and set it up to assign my machine a static IPv4 address.  Then booted into Ubuntu.  None of my changes with the Network Manager seemed to be having an effect, so I decided to setup the interface manually in /etc/network/interfaces .  I discovered there was no entry for my eno1 in the file, it only had an entry for the loopback interface, which is probably why nothing was working.  So, I added the following:

```

auto eno1
iface eno1 inet static
	address 10.0.0.3
	netmask 255.255.255.0
	network 10.0.0.0
	broadcast 10.0.0.255
	gateway 10.0.0.1
	dns-nameservers 10.0.0.1 8.8.8.8

```

After a restart I was the connection worked.

---

### Post by wildmanne39 on 2017-05-29
*Thread moved to **Networking & Wireless**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

If your issue is solved please use thread tools at the top of the page to mark it solved.

Thanks

---

### Post by shridhar-kapshikar on 2017-05-30
[COLOR=#000000][FONT=Arial]First, check to see if IPv6 is already disabled

[/FONT][/COLOR]```
[COLOR=#000000][FONT=Consolas]cat /proc/sys/net/ipv6/conf/all/disable_ipv6[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Consolas]

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]If the return value is 1, then IPv6 is already disabled, and you are done. A return value of 0 indicates IPv6 is active, and you need to continue to next step.

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Open the file [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/etc/sysctl.conf[/FONT][/COLOR][COLOR=#000000][FONT=Arial] in your text editor of choice, [/FONT][/COLOR][COLOR=#000000][FONT=Arial] you will need to have superuser access in order to save your changes.
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]At the end of [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]sysctl.conf[/FONT][/COLOR][COLOR=#000000][FONT=Arial], at the following three lines:
[/FONT][/COLOR]
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```[COLOR=#000000][FONT=Arial]

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Now run [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]sudo sysctl -p[/FONT][/COLOR][COLOR=#000000][FONT=Arial] to update to reconfigure the kernel parameters with the new values [/FONT]set[/COLOR][COLOR=#000000][FONT=Arial] in the previous step

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]If you run [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]/proc/sys/net/ipv6/conf/all/disable_ipv6[/FONT][/COLOR][COLOR=#000000][FONT=Arial] now, it should now return 1 indicating that IPv6 has been disabled.

Then

[/FONT][/COLOR]```
sudo nano /etc/network/interfaces
```[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]and paste this under:# The primary network interface

```

iface en01 inet static
address 192.168.0.16
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.4.4 8.8.8.8
```

[COLOR=#111111][FONT=Ubuntu] restart your networking service to get the ip address,

```

sudo service networking restart

```

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]when you run ifconfig -a - you will able to see ip address assigned to the eno1 interface.


[/FONT][/COLOR]

---

