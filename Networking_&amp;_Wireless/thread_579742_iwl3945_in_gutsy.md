---
title: "iwl3945 in gutsy"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by Zorael on 2007-10-18
I just installed Gutsy and read that the iwl3945 module fixes some problems for users having issues with the older ipw3945 one (read: me).

So I disabled ipw3945 and modprobed iwl3945. It loads fine, but I don't know how to use it.

My wlan interface (eth1) shows as disabled, and I can't bring it up, says the operation is not supported. Furthermore, there's an extra interface now, named wlan0_rename, which has wireless extensions but doesn't show up in ifconfig.

What do I need to do?

---

### Post by Zorael on 2007-10-18
Forgot this:

```
zorael@azrael:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:a0:d1:a0:ec:6b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.0.3 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:6e:39:9a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.13 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

zorael@azrael:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0_rename  IEEE 802.11g  ESSID:"lappskole"
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

zorael@azrael:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:A0:EC:6B
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fea0:ec6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:364476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:261875379 (249.7 MB)  TX bytes:37340068 (35.6 MB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:91061 (88.9 KB)  TX bytes:91061 (88.9 KB)

zorael@azrael:~$ sudo ifconfig eth1 up
SIOCSIFFLAGS: Operation not supported

zorael@azrael:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0_rename  Interface doesn't support scanning : Network is down
```

The kill switch isn't toggled, so that can't be it. Also, it would have said so in iwconfig's output.

---

### Post by Hero of Time on 2007-10-18
What happens if you type 'sude ifup wlan0_rename'? If you want to bring up an interface, be sure to use the right name. Since eth1 is disabled and your wlan adapter got the name wlan0_rename, try that. Also check your interfaces file found in /etc/network/interfaces.

---

### Post by Zorael on 2007-10-18
It didn't want to recognize wlan0_rename as a proper interface, so I couldn't do ifup wlan0_rename or ifconfig wlan0_rename up.

It does now, though, after I put ipw3945 in /etc/modprobe.d/blacklist, put iwl3945 in /etc/modules, and rebooted.

However, it still does not work - everything shows up correct, but it can't scan for networks, and it doesn't associate with my router. :(

(suspicious parts in bold)

```
zorael@azrael:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:A0:EC:6B
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fea0:ec6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1424077 (1.3 MB)  TX bytes:432618 (422.4 KB)
          Interrupt:16

eth1      Link encap:**UNSPEC**  HWaddr 00-18-DE-6E-39-9A-00-00-00-00-00-00-00-00-00-00
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2301 (2.2 KB)  TX bytes:2301 (2.2 KB)

wlan0_ren Link encap:Ethernet  HWaddr 00:18:DE:6E:39:9A
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0_ren Link encap:Ethernet  HWaddr 00:18:DE:6E:39:9A
          inet addr:192.168.0.13  Bcast:0.0.0.0  Mask:0.0.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

zorael@azrael:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0_rename  IEEE 802.11g  ESSID:"lappskole"
          Mode:Managed  Frequency:2.412 GHz  Access Point: **Not-Associated**
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

zorael@azrael:/$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0_rename  **Failed to read scan data : Resource temporarily unavailable**
```


It pauses for exactly 15 seconds before displaying that last "failed to read scan data" message, if that helps...

---

### Post by Hero of Time on 2007-10-18
Ok, I've done some searching and might have come up with a solution. Open the following file with root privileges:
/etc/udev/rules.d/70-persistent-net.rules
In it, you will find the names of your interface cards. Where you see the eth1 interface, put # in front of the line to make it a comment so it will be ignored. Then, locate the other interface name and change it to either eth1 or wlan0 (if it says wlan0_rename).

Disclaimer:
I will NOT take responsibility if you screw up your system. I just tested this with my own ethernet controller and the name changed from eth0 to lan. This is no garantee it works.

---

### Post by Zorael on 2007-10-18
Hmm, okay. There is no entry there for wlan0_rename, only for eth0 and eth1. It seems to me that wlan0_resume is somehow an extension of eth1, which really doesn't make sense to me, at least.

At any rate, I'm not sure fixing that would solve the interface failing to scan for networks. :(

---

### Post by Hero of Time on 2007-10-19
You can't scan, because the interface isn't up. And it isn't up because it's not listed in your interfaces file or named correctly.

What does the entry for eth1 say? I checked your previous posts to see if I missed anything, and at the end of your eth1 mac address is all 00-00... If that is also in the persistent-net.rules file then try to remove them, or copy the line and change the name to wlan0. Perhaps a remove can be done to force a recheck on the interface and add it to the correct files.

This is just speculation, but worth a try.

---

### Post by ebishop on 2007-10-29
I'm not in front of the computer right now, but I have an old laptop with a Microsoft wireless network card with the same problems.  Everything worked fine in Feisty.  I just updated to Gutsy over the weekend.  The networking worked fine during the install, but when I boot up, it has the wlan card named "wlan0_rename", the wireless network doesn't work, and the usual gui network tools don't seem to work with it.  However, when I set up the wireless config from the command line, everything works fine.... I'm not in front of the computer, so these commands are from memory and may be off a little bit.

sudo iwconfig wlan0_rename essid ROUTER
sudo iwconfig wlan0_rename key ABCD123456
sudo dhclient

When I get a chance, I'll play around with the wireless lan card drivers to see if that fixes anything.  If not, I guess my workaround will be to just plug those commands in to the rc.local or try a fresh install.

---

### Post by ebishop on 2007-10-29
I think I have my problem fixed.  My wlan card uses different drivers (I think hermes and/or orinoco).  I don't have a whole lot of experience working with drivers/kernel modules, so these may be completely unrelated problems.  I read somewhere that the hostap module can cause similar problems and to try blacklisting that.  So, in /etc/modprobe.d/blacklist, enter the following lines:

blacklist hostap
blacklist hostap_cs

Reboot and see if that fixes the problem.

---

### Post by David Valentine on 2007-12-03
> **ebishop said:**
>   I read somewhere that the hostap module can cause similar problems and to try blacklisting that.  So, in /etc/modprobe.d/blacklist, enter the following lines:

blacklist hostap
blacklist hostap_cs

Reboot and see if that fixes the problem.
Interestingly, it did fix my problem for my SMC 2632W v1.2 PCMCIA card, even though "hostap" is supposed to be the official Linux driver.  Go figure.

---

### Post by adverick on 2008-04-09
Try this [http://wiki.debian.org/iwlwifi#head-c9ab967d827d9e5de52656b78edab5f349bc70f6](http://wiki.debian.org/iwlwifi#head-c9ab967d827d9e5de52656b78edab5f349bc70f6)

---

### Post by Vermind on 2008-04-16
Hello.
My laptop was also showing the wlan0_rename in ifconfig.
I removed the line talking about eth1 in
```

/etc/udev/rules.d/70-persistent-net.rules
```. then after a```
sudo modprobe -r iwl3945; sudo modprobe iwl3945
``` I looked at the file, and it has an entry for wlan0, with a comment about iwl3945. my interfaces show eth0 and wmaster and wlan0 now. I did this because though my wlan was working using the NetworkManager, it sometimes just went down and I had to bring it up manually using ifconfig iwconfig and iwlist, or do a reboot. I hope this will help to that end. At least it has the right name now.

---

