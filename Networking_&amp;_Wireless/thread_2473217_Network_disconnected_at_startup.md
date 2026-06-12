---
title: "Network disconnected at startup"
date: 2022-03-28
forum: Networking &amp; Wireless
---

### Post by waffen on 2022-03-28
Hello,
I'm using Ubuntu 21.10, every time I start the PC (Ci5 10Gen + 16GB RAM) the network icon in the top right looks disconnected, I need to manually reconnect it. 
Any idea how to fix it?
Thanks!

---

### Post by ngumuntu on 2022-04-01
HI Mario,

If you open a terminal, and enter the command below, what is the output.
```
grep -i renderer /etc/netplan/*.yaml
```

---

### Post by waffen on 2022-04-01
> **ngumuntu said:**
> HI Mario,

If you open a terminal, and enter the command below, what is the output.
```
grep -i renderer /etc/netplan/*.yaml
```

Hello!

This is:

```
mario@mario:~$ grep -i renderer /etc/netplan/*.yaml
  renderer: NetworkManager

```

---

### Post by ngumuntu on 2022-04-01
Hi Mario,

How about the output of:
```
cat /var/log/syslog | grep 'NetworkManager' | grep 'warn'
```

and 

```
cat /var/log/syslog | grep 'NetworkManager' | grep 'fail'
```

---

### Post by waffen on 2022-04-01
OK here's:

```
mario@mario:~$ cat /var/log/syslog | grep 'NetworkManager' | grep 'warn'
Mar 27 11:00:28 mario NetworkManager[989]: <warn>  [1648396828.0522] dns-sd-resolved[7e471fb24b08b554]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 27 11:00:29 mario NetworkManager[989]: <warn>  [1648396829.1801] dns-sd-resolved[7e471fb24b08b554]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 27 11:01:09 mario NetworkManager[989]: <warn>  [1648396869.4387] dns-sd-resolved[7e471fb24b08b554]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 27 11:01:10 mario NetworkManager[989]: <warn>  [1648396870.5391] dns-sd-resolved[7e471fb24b08b554]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 28 09:46:06 mario NetworkManager[1029]: <warn>  [1648478766.5480] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Mar 28 09:46:06 mario NetworkManager[1029]: <warn>  [1648478766.7580] Error: failed to open /run/network/ifstate
Mar 28 09:46:18 mario NetworkManager[1029]: <warn>  [1648478778.5913] dns-sd-resolved[c8d4ae275966f296]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 28 09:46:20 mario NetworkManager[1029]: <warn>  [1648478780.3640] dns-sd-resolved[c8d4ae275966f296]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 28 09:47:31 mario NetworkManager[1029]: <warn>  [1648478851.5618] dns-sd-resolved[c8d4ae275966f296]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 28 09:47:32 mario NetworkManager[1029]: <warn>  [1648478852.6592] dns-sd-resolved[c8d4ae275966f296]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 28 10:28:52 mario NetworkManager[1066]: <warn>  [1648481332.8448] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Mar 28 10:28:53 mario NetworkManager[1066]: <warn>  [1648481333.0436] Error: failed to open /run/network/ifstate
Mar 28 10:29:09 mario NetworkManager[1066]: <warn>  [1648481349.3290] dns-sd-resolved[e1f3e56969436ead]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 28 10:29:10 mario NetworkManager[1066]: <warn>  [1648481350.4474] dns-sd-resolved[e1f3e56969436ead]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 10:27:30 mario NetworkManager[986]: <warn>  [1648567650.5321] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Mar 29 10:27:30 mario NetworkManager[986]: <warn>  [1648567650.7329] Error: failed to open /run/network/ifstate
Mar 29 10:27:41 mario NetworkManager[986]: <warn>  [1648567661.6961] dns-sd-resolved[3dbab3b83e71e713]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 10:27:43 mario NetworkManager[986]: <warn>  [1648567663.5037] dns-sd-resolved[3dbab3b83e71e713]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 10:30:26 mario NetworkManager[986]: <warn>  [1648567826.1301] dns-sd-resolved[3dbab3b83e71e713]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 10:30:27 mario NetworkManager[986]: <warn>  [1648567827.1723] dns-sd-resolved[3dbab3b83e71e713]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 10:32:37 mario NetworkManager[1048]: <warn>  [1648567957.4078] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Mar 29 10:32:37 mario NetworkManager[1048]: <warn>  [1648567957.6044] Error: failed to open /run/network/ifstate
Mar 29 10:32:53 mario NetworkManager[1048]: <warn>  [1648567973.5827] dns-sd-resolved[84f3bc30b546d07b]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 10:32:54 mario NetworkManager[1048]: <warn>  [1648567974.6839] dns-sd-resolved[84f3bc30b546d07b]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 11:41:32 mario NetworkManager[1008]: <warn>  [1648572092.2475] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Mar 29 11:41:32 mario NetworkManager[1008]: <warn>  [1648572092.4452] Error: failed to open /run/network/ifstate
Mar 29 11:41:49 mario NetworkManager[1008]: <warn>  [1648572109.2358] dns-sd-resolved[24fd9e42adc872c3]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 11:41:50 mario NetworkManager[1008]: <warn>  [1648572110.3444] dns-sd-resolved[24fd9e42adc872c3]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 20:51:48 mario NetworkManager[1046]: <warn>  [1648605108.0942] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Mar 29 20:51:48 mario NetworkManager[1046]: <warn>  [1648605108.2999] Error: failed to open /run/network/ifstate
Mar 29 20:52:04 mario NetworkManager[1046]: <warn>  [1648605124.8537] dns-sd-resolved[47508f720261ab40]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 20:52:05 mario NetworkManager[1046]: <warn>  [1648605125.9278] dns-sd-resolved[47508f720261ab40]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 30 09:40:41 mario NetworkManager[990]: <warn>  [1648651241.6269] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Mar 30 09:40:41 mario NetworkManager[990]: <warn>  [1648651241.8259] Error: failed to open /run/network/ifstate
Mar 30 09:40:57 mario NetworkManager[990]: <warn>  [1648651257.1839] dns-sd-resolved[c4af13d30cf30858]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 30 09:40:58 mario NetworkManager[990]: <warn>  [1648651258.3323] dns-sd-resolved[c4af13d30cf30858]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 31 09:25:52 mario NetworkManager[1045]: <warn>  [1648736752.4725] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Mar 31 09:25:52 mario NetworkManager[1045]: <warn>  [1648736752.6768] Error: failed to open /run/network/ifstate
Mar 31 09:26:09 mario NetworkManager[1045]: <warn>  [1648736769.8518] dns-sd-resolved[5b3552fa6ae96992]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 31 09:26:10 mario NetworkManager[1045]: <warn>  [1648736770.9713] dns-sd-resolved[5b3552fa6ae96992]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 09:40:36 mario NetworkManager[1064]: <warn>  [1648824036.3583] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Apr  1 09:40:36 mario NetworkManager[1064]: <warn>  [1648824036.5677] Error: failed to open /run/network/ifstate
Apr  1 09:40:48 mario NetworkManager[1064]: <warn>  [1648824048.3040] dns-sd-resolved[fd22f3ed1a4af60a]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 09:40:49 mario NetworkManager[1064]: <warn>  [1648824049.4069] dns-sd-resolved[fd22f3ed1a4af60a]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 09:45:19 mario NetworkManager[1064]: <warn>  [1648824319.1243] dns-sd-resolved[fd22f3ed1a4af60a]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 09:45:20 mario NetworkManager[1064]: <warn>  [1648824320.2101] dns-sd-resolved[fd22f3ed1a4af60a]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 22:10:07 mario NetworkManager[1026]: <warn>  [1648869007.4959] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Apr  1 22:10:07 mario NetworkManager[1026]: <warn>  [1648869007.6957] Error: failed to open /run/network/ifstate
Apr  1 22:10:19 mario NetworkManager[1026]: <warn>  [1648869019.6232] dns-sd-resolved[6106fd4127de2dc6]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 22:10:19 mario NetworkManager[1026]: <warn>  [1648869019.7991] dns-sd-resolved[6106fd4127de2dc6]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 22:11:18 mario NetworkManager[1026]: <warn>  [1648869078.1758] dns-sd-resolved[6106fd4127de2dc6]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 22:11:19 mario NetworkManager[1026]: <warn>  [1648869079.2548] dns-sd-resolved[6106fd4127de2dc6]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address

```

and:

```
mario@mario:~$ cat /var/log/syslog | grep 'NetworkManager' | grep 'fail'
Mar 27 11:00:28 mario NetworkManager[989]: <warn>  [1648396828.0522] dns-sd-resolved[7e471fb24b08b554]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 27 11:00:29 mario NetworkManager[989]: <warn>  [1648396829.1801] dns-sd-resolved[7e471fb24b08b554]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 27 11:01:09 mario NetworkManager[989]: <warn>  [1648396869.4387] dns-sd-resolved[7e471fb24b08b554]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 27 11:01:10 mario NetworkManager[989]: <warn>  [1648396870.5391] dns-sd-resolved[7e471fb24b08b554]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 28 09:46:06 mario NetworkManager[1029]: <warn>  [1648478766.7580] Error: failed to open /run/network/ifstate
Mar 28 09:46:18 mario NetworkManager[1029]: <warn>  [1648478778.5913] dns-sd-resolved[c8d4ae275966f296]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 28 09:46:20 mario NetworkManager[1029]: <warn>  [1648478780.3640] dns-sd-resolved[c8d4ae275966f296]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 28 09:47:31 mario NetworkManager[1029]: <warn>  [1648478851.5618] dns-sd-resolved[c8d4ae275966f296]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 28 09:47:32 mario NetworkManager[1029]: <warn>  [1648478852.6592] dns-sd-resolved[c8d4ae275966f296]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 28 10:28:53 mario NetworkManager[1066]: <warn>  [1648481333.0436] Error: failed to open /run/network/ifstate
Mar 28 10:29:09 mario NetworkManager[1066]: <warn>  [1648481349.3290] dns-sd-resolved[e1f3e56969436ead]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 28 10:29:10 mario NetworkManager[1066]: <warn>  [1648481350.4474] dns-sd-resolved[e1f3e56969436ead]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 10:27:30 mario NetworkManager[986]: <warn>  [1648567650.7329] Error: failed to open /run/network/ifstate
Mar 29 10:27:41 mario NetworkManager[986]: <warn>  [1648567661.6961] dns-sd-resolved[3dbab3b83e71e713]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 10:27:43 mario NetworkManager[986]: <warn>  [1648567663.5037] dns-sd-resolved[3dbab3b83e71e713]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 10:30:26 mario NetworkManager[986]: <warn>  [1648567826.1301] dns-sd-resolved[3dbab3b83e71e713]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 10:30:27 mario NetworkManager[986]: <warn>  [1648567827.1723] dns-sd-resolved[3dbab3b83e71e713]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 10:32:37 mario NetworkManager[1048]: <warn>  [1648567957.6044] Error: failed to open /run/network/ifstate
Mar 29 10:32:53 mario NetworkManager[1048]: <warn>  [1648567973.5827] dns-sd-resolved[84f3bc30b546d07b]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 10:32:54 mario NetworkManager[1048]: <warn>  [1648567974.6839] dns-sd-resolved[84f3bc30b546d07b]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 11:41:32 mario NetworkManager[1008]: <warn>  [1648572092.4452] Error: failed to open /run/network/ifstate
Mar 29 11:41:49 mario NetworkManager[1008]: <warn>  [1648572109.2358] dns-sd-resolved[24fd9e42adc872c3]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 11:41:50 mario NetworkManager[1008]: <warn>  [1648572110.3444] dns-sd-resolved[24fd9e42adc872c3]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 20:51:48 mario NetworkManager[1046]: <warn>  [1648605108.2999] Error: failed to open /run/network/ifstate
Mar 29 20:52:04 mario NetworkManager[1046]: <warn>  [1648605124.8537] dns-sd-resolved[47508f720261ab40]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 29 20:52:05 mario NetworkManager[1046]: <warn>  [1648605125.9278] dns-sd-resolved[47508f720261ab40]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 30 09:40:41 mario NetworkManager[990]: <warn>  [1648651241.8259] Error: failed to open /run/network/ifstate
Mar 30 09:40:57 mario NetworkManager[990]: <warn>  [1648651257.1839] dns-sd-resolved[c4af13d30cf30858]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 30 09:40:58 mario NetworkManager[990]: <warn>  [1648651258.3323] dns-sd-resolved[c4af13d30cf30858]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 31 09:25:52 mario NetworkManager[1045]: <warn>  [1648736752.6768] Error: failed to open /run/network/ifstate
Mar 31 09:26:09 mario NetworkManager[1045]: <warn>  [1648736769.8518] dns-sd-resolved[5b3552fa6ae96992]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Mar 31 09:26:10 mario NetworkManager[1045]: <warn>  [1648736770.9713] dns-sd-resolved[5b3552fa6ae96992]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 09:40:36 mario NetworkManager[1064]: <warn>  [1648824036.5677] Error: failed to open /run/network/ifstate
Apr  1 09:40:48 mario NetworkManager[1064]: <warn>  [1648824048.3040] dns-sd-resolved[fd22f3ed1a4af60a]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 09:40:49 mario NetworkManager[1064]: <warn>  [1648824049.4069] dns-sd-resolved[fd22f3ed1a4af60a]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 09:45:19 mario NetworkManager[1064]: <warn>  [1648824319.1243] dns-sd-resolved[fd22f3ed1a4af60a]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 09:45:20 mario NetworkManager[1064]: <warn>  [1648824320.2101] dns-sd-resolved[fd22f3ed1a4af60a]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 22:10:07 mario NetworkManager[1026]: <warn>  [1648869007.6957] Error: failed to open /run/network/ifstate
Apr  1 22:10:19 mario NetworkManager[1026]: <warn>  [1648869019.6232] dns-sd-resolved[6106fd4127de2dc6]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 22:10:19 mario NetworkManager[1026]: <warn>  [1648869019.7991] dns-sd-resolved[6106fd4127de2dc6]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 22:11:18 mario NetworkManager[1026]: <warn>  [1648869078.1758] dns-sd-resolved[6106fd4127de2dc6]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address
Apr  1 22:11:19 mario NetworkManager[1026]: <warn>  [1648869079.2548] dns-sd-resolved[6106fd4127de2dc6]: send-updates SetLinkDNS@2 failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid DNS server address

```

---

### Post by praseodym on 2022-04-03
Please run the wireless script from the sticky thread and show the output

---

### Post by ngumuntu on 2022-04-03
Hi Mario,

Here is the link to the sticky thread with the wireless script.

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by waffen on 2022-04-03
Thanks for the help, here's the result:

```

########## wireless info START ##########

Report from: 03 Apr 2022 22:46 -05 -0500

Booted last: 03 Apr 2022 00:00 -05 -0500

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 21.10
Release:	21.10
Codename:	impish

##### kernel ############################

Linux 5.13.0-39-generic #44-Ubuntu SMP Thu Mar 24 15:35:05 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (12) I219-V [8086:0d55]
	DeviceName: Onboard - Ethernet
	Subsystem: Gigabyte Technology Co., Ltd Ethernet Connection (12) I219-V [1458:e000]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 048d:5702 Integrated Technology Express, Inc. ITE Device
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

EFI variables are not supported on this system

##### lsmod #############################

gigabyte_wmi           20480  0
intel_wmi_thunderbolt    20480  0
wmi_bmof               16384  0
wmi                    32768  3 intel_wmi_thunderbolt,gigabyte_wmi,wmi_bmof

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    altname enp0s31f6
    inet 192.168.0.52/24 brd 192.168.0.255 scope global dynamic noprefixroute eno1
       valid_lft 42530sec preferred_lft 42530sec
    inet6 2800:200:e750:3a7:b004:19c0:7030:6d1a/128 scope global dynamic noprefixroute 
       valid_lft 3438sec preferred_lft 3438sec
    inet6 2800:200:e750:3a7:fe8a:1d7d:8f51:2e37/64 scope global temporary dynamic 
       valid_lft 577350sec preferred_lft 58547sec
    inet6 2800:200:e750:3a7:750:1544:bf4e:8cfa/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 15551953sec preferred_lft 2591953sec
    inet6 fe80::387b:c321:65bc:79be/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

##### route #############################

default via 192.168.0.1 dev eno1 proto dhcp metric 100 
169.254.0.0/16 dev eno1 scope link metric 1000 
192.168.0.0/24 dev eno1 proto kernel scope link src 192.168.0.52 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search home

##### network managers ##################

Installed:

	NetworkManager

Running:

root         992       1  0 10:35 ?        00:00:22 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (12) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 5.13.0-39-generic
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/eno1
GENERAL.PATH:                           pci-0000:00:1f.6
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Conexión cableada 1
GENERAL.CON-UUID:                       a52053e5-c581-30c3-bdcd-aa9615bcaa13
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
INTERFACE-FLAGS.PROMISC:                no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.52/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             190.113.220.18
IP4.DNS[2]:                             190.113.220.51
IP4.DNS[3]:                             190.113.220.54
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        broadcast_address = 192.168.0.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 69986
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[4]:                        domain_name = home
DHCP4.OPTION[5]:                        domain_name_servers = 190.113.220.18 190.113.220.51 190.113.220.54
DHCP4.OPTION[6]:                        expiry = 1649086524
DHCP4.OPTION[7]:                        ip_address = 192.168.0.52
DHCP4.OPTION[8]:                        requested_broadcast_address = 1
DHCP4.OPTION[9]:                        requested_domain_name = 1
DHCP4.OPTION[10]:                       requested_domain_name_servers = 1
DHCP4.OPTION[11]:                       requested_domain_search = 1
DHCP4.OPTION[12]:                       requested_host_name = 1
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[15]:                       requested_nis_domain = 1
DHCP4.OPTION[16]:                       requested_nis_servers = 1
DHCP4.OPTION[17]:                       requested_ntp_servers = 1
DHCP4.OPTION[18]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[19]:                       requested_root_path = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       requested_static_routes = 1
DHCP4.OPTION[22]:                       requested_subnet_mask = 1
DHCP4.OPTION[23]:                       requested_time_offset = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       routers = 192.168.0.1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         2800:200:e750:3a7:b004:19c0:7030:6d1a/128
IP6.ADDRESS[2]:                         2800:200:e750:3a7:fe8a:1d7d:8f51:2e37/64
IP6.ADDRESS[3]:                         2800:200:e750:3a7:750:1544:bf4e:8cfa/64
IP6.ADDRESS[4]:                         fe80::387b:c321:65bc:79be/64
IP6.GATEWAY:                            fe80::4a29:52ff:fe3c:cac6
IP6.ROUTE[1]:                           dst = 2800:200:e750:3a7::/64, nh = fe80::4a29:52ff:fe3c:cac6, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::4a29:52ff:fe3c:cac6, mt = 20100
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[4]:                           dst = 2800:200:e750:3a7:b004:19c0:7030:6d1a/128, nh = ::, mt = 100
IP6.DNS[1]:                             2800:200:2000::410
IP6.DNS[2]:                             2800:200:2000::d0
IP6.DNS[3]:                             2800:200:2000::c7
IP6.DNS[4]:                             ::
IP6.SEARCHES[1]:                        home
DHCP6.OPTION[1]:                        dhcp6_domain_search = home
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2800:200:2000::410 2800:200:2000::d0 2800:200:2000::c7
DHCP6.OPTION[3]:                        ip6_address = 2800:200:e750:3a7:b004:19c0:7030:6d1a
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a52053e5-c581-30c3-bdcd-aa9615bcaa13 | Conexión cableada 1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com./

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Lima (based on set time zone)

global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eno1      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############

```

---

### Post by waffen on 2022-04-05
Hello,

I'm adding more info about this problem, here's an screenshot with the first time login screen, you can see the network icon looks like disconnected: (links are from my personal Nextcloud)

[https://cloud.lacunza.biz/index.php/s/RanNp2pDg3xKSYz]("https://cloud.lacunza.biz/index.php/s/RanNp2pDg3xKSYz")


After login and enter into desktop I have this image, I make a ping to my router and no problem, but I don't have any internet connection, I need to manually off -> on the wired connection. My son's pc have no issues, it's a windows 10 PC. 

[https://cloud.lacunza.biz/index.php/s/dBgBJzp6DpWod5N]("https://cloud.lacunza.biz/index.php/s/dBgBJzp6DpWod5N")

In other forum someone suggest this:
```
mario@mario:~$ nmcli device set eno1 autoconnect yes
```

that works for 2 days and the issue start again.

---

