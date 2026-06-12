---
title: "No internet on Ubuntu 17.10"
date: 2018-02-13
forum: Networking &amp; Wireless
---

### Post by klubinus on 2018-02-13
Hi,

I just did a clean install of Ubuntu 17.10 and I can't manage to get internet access, be it over WiFi, Ethernet, Bluetooth or USB tether.

I"m fairly new to Linux but I managed to run the wireless script and got this as a result

[https://pastebin.ubuntu.com/p/VHFWV8dtbH/](https://pastebin.ubuntu.com/p/VHFWV8dtbH/)

I would very much appreciate your help and will try to complement this post as needed 
I also tried reinstalling

---

### Post by chili555 on 2018-02-13
> IP4.ADDRESS[1]:                         192.168.2.9/24
IP4.GATEWAY:                            192.168.2.1
[COLOR="#FF0000"]IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000[/COLOR]
IP4.DNS[1]:                             10.221.10.18
IP4.DNS[2]:                             10.221.9.26
IP4.DNS[3]:                             192.168.0.1I'm not sure I understand that at all. What do these terminal commands tell us?```
route -n
ping -c3 192.168.2.1
ping -c3 8.8.8.8
```Do other devices on the same network, phones, pods, pads, etc., connect correctly?

---

### Post by klubinus on 2018-02-13
All devices on the same network, phones and Desktop pcs, connect just fine,

---

### Post by chili555 on 2018-02-13
> **klubinus said:**
> All devices on the same network, phones and Desktop pcs, connect just fine,How about the results of the terminal commands?

---

### Post by klubinus on 2018-02-13
```
klaus@Klinux:~$ ping -c3 192.168.2.1PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=44.5 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=1.40 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=1.35 ms


--- 192.168.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.359/15.761/44.515/20.332 ms
klaus@Klinux:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=59 time=22.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=59 time=10.6 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=59 time=5.23 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 5.236/12.697/22.221/7.086 ms
klaus@Klinux:~$ route -n
The program 'route' is currently not installed. You can install it by typing:
sudo apt install net-tools



```

I think I might be doing something wrong but here is the terminal output

---

### Post by chili555 on 2018-02-13
> klaus@Klinux:~$ route -n
The program 'route' is currently not installed. You can install it by typing:
sudo apt install net-toolsVery strange.

Please do:```
sudo dpkg-reconfigure resolvconf
```
Say yes to "prepare /etc/resolve.conf for dynamic updates?" and reboot.

Now try: ```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```Any improvement?

I hope we don't find that the missing net-tools is the real problem!

---

### Post by klubinus on 2018-02-13
well...

```
klaus@Klinux:~$ sudo dpkg-reconfigure resolvconf[sudo] password for klaus: 
Sorry, try again.
[sudo] password for klaus: 
dpkg-query: package 'resolvconf' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: resolvconf is not installed
klaus@Klinux:~$ 



```

---

### Post by chili555 on 2018-02-13
resolvcong and net-tools missing? I wonder how much else is wrong. I suggest that you download a fresh new copy of 17.10 and reinstall. [https://www.ubuntu.com/desktop/1710](https://www.ubuntu.com/desktop/1710)

I honestly feel that it would take longer and be more difficult to repair this than to start new.

---

### Post by klubinus on 2018-02-13
Could it be the program I'm using to flash the USB?  I'm using Rufus on win10  honestly its the only thing I can think of...

---

### Post by chili555 on 2018-02-13
> **klubinus said:**
> Could it be the program I'm using to flash the USB?  I'm using Rufus on win10  honestly its the only thing I can think of...I doubt it. I think the .iso that you originally downloaded was corrupt. The fact that the problem remains after you reinstalled seems to confirm it. That's why I suggested that you download a completely new fresh copy. [http://mirror.pnl.gov/releases/17.10/](http://mirror.pnl.gov/releases/17.10/)

Notice that md5sums, sha256sums, etc. are available to verify the integrity of the download. I don't know much about Windows 10 so I can't tell you how to accomplish this in Windows.

---

