---
title: "Netgear WNA 3100 (v.1) Wireless N-300 not working with 18.04"
date: 2018-06-04
forum: Networking &amp; Wireless
---

### Post by bvargo on 2018-06-04
I know this is a perennial favorite and so with the new version of Ubuntu I am wondering if anyone has gotten this working.  
I can see the USB device and I have the 64-bit driver installed in ndiswrapper but the computer won't see the network device:
```

bvargo@HP:~$ sudo lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

bvargo@HP:~$ sudo ndiswrapper -l
bcmwlhigh6 : driver installed
	device (0846:9020) present

bvargo@HP:~$ sudo modprobe ndiswrapper

bvargo@HP:~$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf

bvargo@HP:~$ sudo modprobe ndiswrapper

bvargo@HP:~$ ifconfig
enp: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.29  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::b2ec:8c2:d20f:708a  prefixlen 64  scopeid 0x20<link>
        ether 00:1e:0b:b6:25:27  txqueuelen 1000  (Ethernet)
        RX packets 1328579  bytes 558558504 (558.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1987935  bytes 195131157 (195.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  memory 0xf0100000-f0120000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 13922  bytes 1170574 (1.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 13922  bytes 1170574 (1.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

bvargo@HP:~$ iwconfig
lo        no wireless extensions.


enp   no wireless extensions.

```


Thoughts?

---

### Post by praseodym on 2018-06-04
Please check
```

dmesg | egrep 'ndis|key'
```

---

### Post by chili555 on 2018-06-04
Please check here: [https://ubuntuforums.org/showthread.php?t=2264020&highlight=wna3100](https://ubuntuforums.org/showthread.php?t=2264020&highlight=wna3100)> As of now, unless someone has another driver or process to try, I don't believe this device can be made to work correctly in Ubuntu 14.04 and later. Please don't ask me to help. I've tried everything I know of and it doesn't work.
Frankly, I haven't seen ndiswrapper work correctly in several years. 

I'm sorry that you picked one of the very few devices that I am aware of that can't be made to work in Linux at all.

---

