---
title: "Wifi gone on Lenovo E550 and Ubuntu 16.10"
date: 2017-05-15
forum: Networking &amp; Wireless
---

### Post by debzsud on 2017-05-15
Hi,

Since this morning my WIFI has passed away. In the indicator on the tool bar, I don't get any wifi suggested.
I'm on a portable PC ThinkPad Lenovo E550 using Ubuntu 16.10. My wired connection still work. I can't really remember doing any update or whatever important this morning but the fact that the computer became hot after staying in the sun.   
 Here are some output:

```

>> ifconfig
enp0s25: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.197  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::27cd:e778:9ecc:7fdb  prefixlen 64  scopeid 0x20<link>
        ether c8:5b:76:10:5b:d3  txqueuelen 1000  (Ethernet)
        RX packets 42434  bytes 38869114 (38.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 32672  bytes 3682261 (3.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf1100000-f1120000  
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 2809  bytes 234262 (234.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2809  bytes 234262 (234.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

>> iwconfig
enp0s25   no wireless extensions.
lo        no wireless extensions.

>> rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

I don't really know what to try now. Any suggestion ?

---

