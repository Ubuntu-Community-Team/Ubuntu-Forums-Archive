---
title: "No wlan0 device (Intel ipw3945)"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by mrborisguy on 2007-07-15
I can not seem to get my wireless connection to work. I have been following the various How To's for Ubuntu, but nothing works. The problem is that wlan0 never shows up is ifconfig -a or iwconfig. When I do ifconfig -a, I only get entries for eth0 (my wired connection) and lo.

First, this is the wireless card that I have, which came with my laptop.

```
bryan@bryan:~$ lspci | grep -i wireless
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

If I use the Intel driver:

```
bryan@bryan:~$ sudo modprobe ipw3945
bryan@bryan:~$ lsmod | grep ipw3945
ipw3945               118816  0 
ieee80211              34760  1 ipw3945
```

I can see that the module loaded, but still only eth0 and lo show up in my ifconfig -a.

```
eth0      Link encap:Ethernet  HWaddr 00:16:D4:3A:13:C4  
          inet addr:192.168.20.35  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe3a:13c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1301320 (1.2 MiB)  TX bytes:218521 (213.3 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13900 (13.5 KiB)  TX bytes:13900 (13.5 KiB)
```

So, I try to use the ndiswrapper method instead:

```
bryan@bryan:~$ sudo rmmod ipw3945
bryan@bryan:~$ sudo ndiswrapper -i /home/common/SWSETUP/WLAN2/W3945-2915-2200/w39n51.inf
installing w39n51 ...
bryan@bryan:~$ ndiswrapper -l
w39n51 : driver installed
        device (8086:4222) present (alternate driver: ipw3945)
bryan@bryan:~$ sudo modprobe ndiswrapper
bryan@bryan:~$ lsmod | grep ndiswrapper
ndiswrapper           194608  0 
usbcore               134280  6 ndiswrapper,hci_usb,usbhid,uhci_hcd,ehci_hcd
```

Again, the ndiswrapper module was loaded, but again, only eth0 and lo show up in my ifconfig -a.
(Note, the .inf file is the original that came with the computer when I purchased it.)

```
eth0      Link encap:Ethernet  HWaddr 00:16:D4:3A:13:C4  
          inet addr:192.168.20.35  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe3a:13c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1301320 (1.2 MiB)  TX bytes:218521 (213.3 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13900 (13.5 KiB)  TX bytes:13900 (13.5 KiB)
```

At one point, I did manage to get wlan0 to show up in ifconfig -a using the ndiswrapper steps, but I have not been able to reproduce that despite reboots and a variety of tries.

Does anybody know what my problem could be?

---

### Post by Rebeca on 2007-07-15
Maybe this will solve your problem: [http://ubuntuforums.org/showpost.php?p=3009797&postcount=3](http://ubuntuforums.org/showpost.php?p=3009797&postcount=3)

---

### Post by SundeepG on 2007-07-16
> **mrborisguy said:**
> I can not seem to get my wireless connection to work. I have been following the various How To's for Ubuntu, but nothing works. The problem is that wlan0 never shows up is ifconfig -a or iwconfig. When I do ifconfig -a, I only get entries for eth0 (my wired connection) and lo.

I am running Ubuntu 7.04 and an Intel 3945ABG wireless adapter. I have an ethernet port listed as eth0, and my wireless card actually comes up as eth1 instead of wlan0. Have u tried to see if this is the case for u?

Also, I am getting much slower downstream in Ubuntu than I do in Windows for some reason, do u know anything about this?

---

### Post by t4thfavor on 2007-07-16
I have the same card, and it also doesnt show up as wifi0. It shows as an ethX, but only when the hardware wireless switch is on. When the switch is off no device shows up.
Depending on your laptop model, you will have to find out where your killswitch is (assuming you have one), and turn it on.

---

