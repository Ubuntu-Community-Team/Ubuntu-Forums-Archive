---
title: "Upgraded to Ubuntu 17.10 - no internet"
date: 2017-10-19
forum: Networking &amp; Wireless
---

### Post by marco-frg on 2017-10-19
Hi,

I have upgraded from 17.04 to Ubuntu 17.10 and unfortunately no Wifi or Ethernet does work anymore. (Wifi does not detect any networks, ethernet seems connected but no internet).

I've attached my network config....hope anybody could help me ?

Thanks a lot !

---

### Post by chili555 on 2017-10-19
Your settings in /etc/network/interfaces are faulty. Please correct the file. From the terminal:```
sudo nano /etc/network/interfaces
```Change the file to read:```
auto lo
iface lo inet loopback
```Proofread carefully, save and close the text editor. Reboot and show us:```
ifconfig
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```Thanks.

---

### Post by Hadaka on 2017-10-19
Hi, you can use nano to edit your /etc/network/interfaces file
  as The good Dr chili555 suggested or you can...
*remove current file
```
sudo rm /etc/network/interfaces
```
*Rewrite file
```
echo -e "auto lo\niface lo inet loopback" | sudo tee -a /etc/network/interfaces
```
*Avoid 17.04/17.10 possible bug..Please do..
```
printf "[device]\nwifi.scan-rand-mac-address=0\n"| sudo tee -a /etc/NetworkManager/*.conf
```
*Power managementis on [IWCONFIG] and should be off. Please do..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
*Country code currently -Unset 00- [REGION--> Europe/Berlin]Please do..
```
sudo iw reg set DE
sudo sed -i 's/=.*/=DE/' /etc/default/crda
```
and the pings as Dr chili555 requested.
Thanks.

---

### Post by ynota on 2017-10-20
Marco-frg,
            Your problem is that you have your WIFI connection set up manually with a static address in /etc/network/interfaces and your wired Ethernet connection setup in network manager. You can use one or the other but not both, as with the above replies, the simplest way to fix this problem is to remove your static setup in /etc/network/interfaces. if you would rather use WIFI with network manager then configure it in network manager and remove the wired setup.

---

### Post by marco-frg on 2017-10-20
Hi,

thx for the quick replys. I can now connect to Wifi again but I guess DNS is not working. I've tried to manually 8.8.8.8 as DNS server in the network manager (gui) but that did not help. Attached are the requested ping results.

---

### Post by Hadaka on 2017-10-20
Hi, thanks for the information. Please provide the output of the
ping requests in a regular text type copy and paste. Most of us
will not open an unknown .zip file
please post the output of..
```
ifconfig
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```
Thanks.

---

### Post by marco-frg on 2017-10-20
Ok,

```

ifconfig
enp0s31f6: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.178  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::989d:d4b8:3e02:e9c5  prefixlen 64  scopeid 0x20<link>
        ether 70:4d:7b:6f:eb:98  txqueuelen 1000  (Ethernet)
        RX packets 81  bytes 9867 (9.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 161  bytes 17834 (17.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xdf300000-df320000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1178  bytes 89955 (89.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1178  bytes 89955 (89.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.100  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::df02:6481:72cd:e70c  prefixlen 64  scopeid 0x20<link>
        ether 10:be:f5:07:4d:c6  txqueuelen 1000  (Ethernet)
        RX packets 144  bytes 19347 (19.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 116  bytes 15696 (15.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


=========================


PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.26 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=2.34 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.22 ms


--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 1.220/1.608/2.341/0.519 ms




================================================================00
ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=58 time=11.5 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=58 time=10.5 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=58 time=11.5 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 10.515/11.202/11.549/0.493 ms




=================================================00


ping -c3 www.ubuntu.com
ping: www.ubuntu.com: Name or service not known



```

---

### Post by wardzilla on 2017-10-20
Hi,

I was having the same issue.

The solution from this post resolved it for me:

[https://askubuntu.com/questions/622470/dns-probe-finished-bad-config-error-in-ubuntu-14-04](https://askubuntu.com/questions/622470/dns-probe-finished-bad-config-error-in-ubuntu-14-04)

---

### Post by marco-frg on 2017-10-20
Thx wardzilla ! Resolved :)

---

### Post by darkwa on 2017-12-20
The solution on this video worked for me:
[https://www.youtube.com/watch?v=GOeF2sKQm_M](https://www.youtube.com/watch?v=GOeF2sKQm_M)

---

### Post by fv7 on 2018-01-12
The second option in [https://askubuntu.com/a/882812/682596](https://askubuntu.com/a/882812/682596) fixed it for me.

---

