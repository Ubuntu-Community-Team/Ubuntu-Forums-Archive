---
title: "Wifi Detection and connection problem"
date: 2018-10-07
forum: Networking &amp; Wireless
---

### Post by pratikcsc on 2018-10-07
I am using Ubuntu since long years. I was working on Ubuntu 16.04 and recently upgraded into Ubuntu 18.04. I am using HP laptop of series hp-15-be016tu. I am facing wifi detection issues since starting days but it could be solved using two commands like
1) sudo modprobe -rv rtl8723be
2) sudo modprobe rtl8723be ant_sel=1 or sudo modprobe rtl8723be ant_sel=2

as my network product is RTL8723BE PCIe Wireless Network Adapter
and vendor is Realtek Semiconductor Co., Ltd.

But after upgrading to 18.04 i am facing several issues.
1) only few wifi network are shown (like my home wifi is not shown)
2) some times home wifi network discovers but there was a problem on connection and connection could not be established
3) other wifi connection like android hotspot working great.

---

### Post by praseodym on 2018-10-07
Please show the outputs of these commands:
```

ifconfig -a
iwconfig
iwlist chan
dmesg | grep country
```
Which country do you live?

---

### Post by pratikcsc on 2018-10-07
trap@trap-lappy:~$ ifconfig -a
enp1s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 40:b0:34:c0:e0:b7  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5161  bytes 507509 (507.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5161  bytes 507509 (507.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.43.143  netmask 255.255.255.0  broadcast 192.168.43.255
        inet6 2405:204:4402:1816:bfa9:f27c:76ec:6dd9  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::68e7:e678:d06b:333e  prefixlen 64  scopeid 0x20<link>
        ether 3c:a0:67:fe:6e:05  txqueuelen 1000  (Ethernet)
        RX packets 355507  bytes 462526882 (462.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 224804  bytes 28280124 (28.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

trap@trap-lappy:~$ iwconfig
lo        no wireless extensions.

wlo1      IEEE 802.11  ESSID:"Trap's Phone"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 80:AD:16:8F:44:CE   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4418   Missed beacon:0

enp1s0    no wireless extensions.

trap@trap-lappy:~$ iwlist chan
lo        no frequency information.

wlo1      13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

enp1s0    no frequency information.

trap@trap-lappy:~$ dmesg | grep country
trap@trap-lappy:~$

---

### Post by praseodym on 2018-10-07
Deactivate the power management
```

sudo iwconfig wlo1 power off
```

---

