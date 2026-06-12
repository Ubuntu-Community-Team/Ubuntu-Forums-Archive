---
title: "Disconnected - you are now offline"
date: 2023-09-09
forum: Networking &amp; Wireless
---

### Post by peyre on 2023-09-09
Something went wrong with my Xubuntu desktop this morning.  Certain things suddenly didn't look right, including the Whisker menu button (equiv. of Start button) showed a generic icon rather than the usual mouse head.  So I rebooted, and when it came up it refused to accept my password.  I did Ctrl-Alt-F3 and was able to sign in at a command prompt.  I tried a number of things, finally running sudo apt reinstall xubuntu-desktop.  Now I can sign back into the GUI and everything seems to be working, except networking.  The networking icon in the bottom right shows Enable Networking checked.  If I uncheck it and recheck it I get the notification "Disconnected - you are now offline" and the networking icon still shows disconnected.

This is a desktop with no WiFi connection; it's on ethernet.  The lights on the NIC are blinking, and also on the switch port that the cable's plugged into.  I probably just need to reinstall the networking components or something, but don't know how to go about this.

Edit: Hang on, it seems to have repaired itself!  Odd.

---

### Post by #&amp;thj^% on 2023-09-09
Can you try this to get a active Network
```
sudo dhclient eth0
```
Change eth0 to your correct device.
Then try to reinstall 
```
sudo apt install --reinstall network-manager
```

---

### Post by peyre on 2023-09-10
Thanks for replying to me!  It turns out this problem **didn't** solve itself.  My NIC seems to have been uninstalled or something.  There are now no lights on the NIC or the port on the switch, and (of course) I have no network or Internet connectivity.  Luckily I have a USB WiFi adapter so I can get connectivity, but I don't want to rely on wireless when the machine's sitting *right next* to the switch that's connected to the router.  Also this wireless connection is surprisingly slow and unreliable!  I wonder if my TCP/IP stack is messed up or something.

Sorry, I didn't include the results of what you suggested.  This connection is so slow I hit Edit and went to do other things while it took its sweet time coming up...

sudo dhclient eth0 returned:
Cannot find device "eth0"
cat: /sys/class/net/eth0/ifindex: No such file or directory

so it seems my NIC has been uninstalled or something!  sudo apt install --reinstall network-manager seems to have run successfully, but hasn't made a difference.

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 2,203 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 network-manager amd64 1.36.6-0ubuntu2 [2,203 kB]
Fetched 2,203 kB in 1s (1,667 kB/s)        
(Reading database ... 272245 files and directories currently installed.)
Preparing to unpack .../network-manager_1.36.6-0ubuntu2_amd64.deb ...
Unpacking network-manager (1.36.6-0ubuntu2) over (1.36.6-0ubuntu2) ...
Setting up network-manager (1.36.6-0ubuntu2) ...
Processing triggers for dbus (1.12.20-2ubuntu4.1) ...
Processing triggers for man-db (2.10.2-1) ...

**sudo debsums -sa** returns this.  Should I reinstall libgtk-3-0 and procps?

debsums: changed file /etc/gtk-3.0/settings.ini (from libgtk-3-0:amd64 package)
debsums: changed file /etc/sysctl.conf (from procps package)

Oh, if it matters - lspci shows the following for my NIC:

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)

---

### Post by jeremy31 on 2023-09-10
Results for ```
lspci -nnk |grep-iA3 net; ifconfig
```

---

### Post by peyre on 2023-09-10
Here:
> bash: grep-iA3: command not found
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 22974  bytes 2020538 (2.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 22974  bytes 2020538 (2.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx7cdd90b04306: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.98  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2600:1702:3651:2910:c0cd:5173:956e:307b  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::a34e:3aa7:1a2b:6a66  prefixlen 64  scopeid 0x20<link>
        inet6 2600:1702:3651:2910::62f  prefixlen 128  scopeid 0x0<global>
        inet6 2600:1702:3651:2910:623b:f0b5:a15c:c29  prefixlen 64  scopeid 0x0<global>
        ether 7c:dd:90:b0:43:06  txqueuelen 1000  (Ethernet)
        RX packets 309669  bytes 211136284 (211.1 MB)
        RX errors 0  dropped 6692  overruns 0  frame 0
        TX packets 193817  bytes 80105216 (80.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


---

### Post by jeremy31 on 2023-09-10
Results for ```
lspci -nnk |grep -iA3 net; ifconfig
```

---

### Post by peyre on 2023-09-10
Here:
> bash: grep-iA3: command not found
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 22974  bytes 2020538 (2.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 22974  bytes 2020538 (2.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx7cdd90b04306: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.98  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2600:1702:3651:2910:c0cd:5173:956e:307b  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::a34e:3aa7:1a2b:6a66  prefixlen 64  scopeid 0x20<link>
        inet6 2600:1702:3651:2910::62f  prefixlen 128  scopeid 0x0<global>
        inet6 2600:1702:3651:2910:623b:f0b5:a15c:c29  prefixlen 64  scopeid 0x0<global>
        ether 7c:dd:90:b0:43:06  txqueuelen 1000  (Ethernet)
        RX packets 309669  bytes 211136284 (211.1 MB)
        RX errors 0  dropped 6692  overruns 0  frame 0
        TX packets 193817  bytes 80105216 (80.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


---

### Post by jeremy31 on 2023-09-10
Add a space between grep and -iA3 net

---

### Post by peyre on 2023-09-10
Oh!  Here you go.

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
	Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
	Kernel driver in use: r8169
	Kernel modules: r8169
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 23912  bytes 2135672 (2.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 23912  bytes 2135672 (2.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx7cdd90b04306: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.98  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2600:1702:3651:2910:c0cd:5173:956e:307b  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::a34e:3aa7:1a2b:6a66  prefixlen 64  scopeid 0x20<link>
        inet6 2600:1702:3651:2910::62f  prefixlen 128  scopeid 0x0<global>
        inet6 2600:1702:3651:2910:623b:f0b5:a15c:c29  prefixlen 64  scopeid 0x0<global>
        ether 7c:dd:90:b0:43:06  txqueuelen 1000  (Ethernet)
        RX packets 371932  bytes 241477543 (241.4 MB)
        RX errors 0  dropped 9325  overruns 0  frame 0
        TX packets 242127  bytes 92275911 (92.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

---

### Post by peyre on 2023-09-10
Oh!  Here you go.

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
	Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
	Kernel driver in use: r8169
	Kernel modules: r8169
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 23912  bytes 2135672 (2.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 23912  bytes 2135672 (2.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx7cdd90b04306: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.98  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2600:1702:3651:2910:c0cd:5173:956e:307b  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::a34e:3aa7:1a2b:6a66  prefixlen 64  scopeid 0x20<link>
        inet6 2600:1702:3651:2910::62f  prefixlen 128  scopeid 0x0<global>
        inet6 2600:1702:3651:2910:623b:f0b5:a15c:c29  prefixlen 64  scopeid 0x0<global>
        ether 7c:dd:90:b0:43:06  txqueuelen 1000  (Ethernet)
        RX packets 371932  bytes 241477543 (241.4 MB)
        RX errors 0  dropped 9325  overruns 0  frame 0
        TX packets 242127  bytes 92275911 (92.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

---

### Post by #&amp;thj^% on 2023-09-10
While you wait for Uncle Jeremy
What is the real name of Ethernet device:
```
ip a | grep eno* && ip a | grep eth0*

```:

---

### Post by jeremy31 on 2023-09-10
Any results for ```
sudo dmesg|grep r8169
```

---

### Post by peyre on 2023-09-10
**ip a | grep eno* && ip a | grep eth0***
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
2: enp3s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
7: wlx7cdd90b04306: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:24:1d:1d:b7:33 brd ff:ff:ff:ff:ff:ff
    link/ether 7c:dd:90:b0:43:06 brd ff:ff:ff:ff:ff:ff

**sudo dmesg|grep r8169**
[    1.625165] r8169 0000:03:00.0 eth0: RTL8168c/8111c, 00:24:1d:1d:b7:33, XID 3c4, IRQ 24
[    1.625174] r8169 0000:03:00.0 eth0: jumbo features [frames: 6122 bytes, tx checksumming: ko]
[    1.760588] r8169 0000:03:00.0 enp3s0: renamed from eth0

---

### Post by jeremy31 on 2023-09-10
```
sudo ifconfig enp3s0 up
```
Do any good?

---

### Post by peyre on 2023-09-10
Hey, that seems to have fixed it!  I had to **dhclient -r** and **sudo dhclient**, but I have connectivity again!

---

### Post by #&amp;thj^% on 2023-09-10
Please keep us posted, so far so good....

---

### Post by peyre on 2023-09-10
Thanks, will do.  Anything I should wait on before marking this as fixed?

---

### Post by #&amp;thj^% on 2023-09-10
Just a day or two, should be good, >>until the next mishap....LOL

---

### Post by peyre on 2023-09-10
Thanks!  I'll hang onto it for now, then.

---

### Post by peyre on 2023-09-11
Oh no, I got home tonight, and I'm offline again.  Every time I restart the computer, the NIC goes dead. :(

Everything is fine if I run **dhclient -r** followed by **sudo dhclient**, but then next time I boot up, NIC is dead again and I have to enter that at a terminal.  It's a workaround for now, but hardly a longer-term solution.

---

### Post by peyre on 2023-09-14
No love this time?  :(

---

