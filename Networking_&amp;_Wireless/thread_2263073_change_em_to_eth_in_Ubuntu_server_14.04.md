---
title: "change em to eth in Ubuntu server 14.04"
date: 2015-01-29
forum: Networking &amp; Wireless
---

### Post by mk-ned on 2015-01-29
hello all

I installed ubuntu 14.04 server on machine which have 4 embedded NIC 
```

lspci -D | grep -i ether
0000:01:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
0000:01:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
0000:02:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)

```
and I find out that they are defined as em's
```

ifconfig -a | grep em
em1       Link encap:Ethernet  HWaddr 00:24:e8:3c:ed:a0  
em2       Link encap:Ethernet  HWaddr 00:24:e8:3c:ed:a2  
em3       Link encap:Ethernet  HWaddr 00:24:e8:3c:ed:a4  
em4       Link encap:Ethernet  HWaddr 00:24:e8:3c:ed:a6

```
I was wondering change em to eth, made search in google and find out that I should modify /etc/udev/rules.d/70-persistent-net.rules
but 70-persistent-net.rules does not exist on my system.
and the second solution which I found was that I should add "biosdevname=0"  in /etc/default/grub and than I should updat grub with update-grub2 to restore it back to eth0. but I don't exactly know on which line should I add it and I am not sure if it is a correct solution.

**[SIZE=4]so how should I change em to eth? what is the correct solution of it?[/SIZE]**

and second question

as I mentioned above there are 4 NIC's,but only one is up.

```

lshw -C network
em1       Link encap:Ethernet  HWaddr 00:24:e8:3c:ed:a0  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fe3c:eda0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1042651 (1.0 MB)  TX bytes:5686 (5.6 KB)

em2       Link encap:Ethernet  HWaddr 00:24:e8:3c:ed:a2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

em3       Link encap:Ethernet  HWaddr 00:24:e8:3c:ed:a4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

em4       Link encap:Ethernet  HWaddr 00:24:e8:3c:ed:a6  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

```

**[SIZE=4]how can I start up others? [/SIZE]**e.g "ifconfig em2 up" starts it up but it does not get "inet addr:"

Best regards MK

---

### Post by slickymaster on 2015-01-29
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by tjiagoM on 2015-04-08
(Similar question here: [http://ubuntuforums.org/showthread.php?t=2263104](http://ubuntuforums.org/showthread.php?t=2263104))

Hello,

I had the same problem as you (I had a em1 NIC instead of a normal eth0). After trying several things, the one that solved my problem was this:

Edit /etc/default/grub and find these lines:
[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""[/FONT]

Add biosdevname=0, just like this:
[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="biosdevname=0"
GRUB_CMDLINE_LINUX="biosdevname=0"[/FONT]

Then run:
[FONT=courier new]sudo update-grub
sudo reboot[/FONT]

At least this worked for me. After that I modified the /etc/network/interfaces in order to have the IP I wanted for eth0.
If this didn't work for you, I also made some changes before this, maybe they could work for you:

[B]First try
[/B]Get your MAC address like you did or with this command (look for the serial attribute):
[FONT=courier new]sudo lshw -class network[/FONT]
Then:
[FONT=courier new]cd /etc/udev/rules.d
sudo nano 70-persistent-net.rules[/FONT]
Add this(substitute the xx:xx:xx:xx:xx with your MAC address. I don't know if dev_id should be the physical id of the "lshw" command):
[FONT=courier new]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:xx:xx:xx:xx:xx", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"[/FONT]
And reboot!


**Second try**
[FONT=courier new]sudo cp /lib/udev/rules.d/75-persistent-net-generator.rules /etc/udev/rules.d/
cd /etc/udev/rules.d
sudo nano 75-persistent-net-generator.rules[/FONT]
And add at the end this(substitute xx:xx:xx with the first part of your MAC address):
[FONT=courier new]ENV{MATCHADDR}==”xx:xx:xx:*”, GOTO=”globally_administered_whitelist”[/FONT]
And reboot!

---

### Post by michi1983 on 2015-04-08
> **mk-ned said:**
> 
e.g "ifconfig em2 up" starts it up but it does not get "inet addr:"


Please post the output of ```
cat /etc/network/interfaces
``` and tell us how do you get your IP addresses?
Do you want to define them static or do you have a DHCP server which serves you with addresses?

---

