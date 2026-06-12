---
title: "Lost network with working network adapter"
date: 2022-11-12
forum: Networking &amp; Wireless
---

### Post by hakelm on 2022-11-12
Suddenly I lost networking on my Ubuntu 20.04 PC.
My network adapter works properly shown by running Ubuntu 20.04 from a live USB-stick.
Networking also works from both Ubuntu and Windows VM-ware guests.
The network icon normally shown at the upper right hand corner of my desktop is replaced by a question-mark.
Further ifconfig tells me networking is up and running, se below.
Obviously something happened to my software but I am at total loss to figure out what.
Any tip is appreciated.
H

root@20:/home/he# ifconfig 
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.4  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::5b18:6f16:ad7b:9504  prefixlen 64  scopeid 0x20<link>
        ether 74:d4:35:88:b0:0f  txqueuelen 1000  (Ethernet)
        RX packets 114831  bytes 166768010 (166.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11523  bytes 1419579 (1.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

---

### Post by chili555 on 2022-11-12
Please run the terminal commands:

```
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ls -al /etc/resolv.conf
```

Please post the results.

---

### Post by hakelm on 2022-11-13
he@20:~$ ping -c3 192.168.1.1; ping -c3 8.8.8.8; ls -al /etc/resolv.conf
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.


--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2048ms


PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2028ms


lrwxrwxrwx 1 root root 39 maj 10  2022 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf


Do you know any write up or description of the networking architecture/software?

---

### Post by chili555 on 2022-11-13
> Do you know any write up or description of the networking architecture/software?I do not.

Let's look at:

```
journalctl -S today | grep Network

sudo dmesg | grep -e Network -e enp3s0
```

---

### Post by hakelm on 2022-11-13
root@20:~# dmesg|grep -e Network  -e enp3s0
[    0.749692] r8169 0000:03:00.0 enp3s0: renamed from eth0
[    5.974690] r8169 0000:03:00.0 enp3s0: Link is Down
[    9.134786] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[    9.134799] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  167.570854] device enp3s0 entered promiscuous mode
[  167.570922] bridge-enp3s0: enabled promiscuous mode
[ 1637.426165] r8169 0000:03:00.0 enp3s0: Link is Down
[ 1638.361527] r8169 0000:03:00.0 enp3s0: Link is Down
[ 1639.087591] device enp3s0 left promiscuous mode
[ 1639.087642] bridge-enp3s0: disabled promiscuous mode
[ 1640.954253] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[ 1640.954409] device enp3s0 entered promiscuous mode
[ 1640.954447] bridge-enp3s0: enabled promiscuous mode
root@20:~#

---

### Post by hakelm on 2022-11-13
[ 5.974690] r8169 0000:03:00.0 enp3s0: Link is Down
is most likely when the PC is suspended
H

---

### Post by chili555 on 2022-11-13
> device enp3s0 entered promiscuous modeAs well as:> [COLOR="#FF0000"]bridge[/COLOR]-enp3s0: enabled promiscuous modeThat's not the usual mode used to send and receive internet traffic, is it?

Please explain.

---

### Post by hakelm on 2022-11-13
Can't explain but I have tried 
ifconfig enp3s0 -promisc
but to no avail
H

---

### Post by chili555 on 2022-11-13
Is your networking configured solely in Network Manager or netplan or (shudder) both?

May we see:

```
cat /etc/netplan/*.yaml
```

Have you been running wireshark or some other sniffing software?

---

### Post by hakelm on 2022-11-14
he@20:~$ cat /etc/netplan/*.yaml
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
he@20:~$

---

### Post by chili555 on 2022-11-14
> **hakelm said:**
> Can't explain but I have tried 
ifconfig enp3s0 -promisc
but to no avail
H
Please try:

```
sudo ifconfig enp3s0 down
sudo ifconfig enp3s0 -promisc
sudo ifconfig enp3s0 up

```
Any improvement?

---

### Post by hakelm on 2022-11-14
Sorry being late but [https://ubuntuforums.org/](https://ubuntuforums.org/) was inaccessible for the major part of today.

sudo ifconfig enp3s0 down
sudo ifconfig enp3s0 -promisc
sudo ifconfig enp3s0 up

had no effect,
H

---

