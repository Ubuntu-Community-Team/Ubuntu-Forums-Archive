---
title: "Getting WiFi USB Adapter to start in master mode (atheros AR9271 chipset)"
date: 2019-09-04
forum: Networking &amp; Wireless
---

### Post by mnewber1 on 2019-09-04
I have an ALFA Network Adapter using the Atheros AR9271 chipset and I want this adapter to act as a Access Point so that I can control multiple GoPros from it using this ([https://github.com/vmayoral/GoProController/blob/master/Infrastructure%20Wifi%20Research.md](https://github.com/vmayoral/GoProController/blob/master/Infrastructure%20Wifi%20Research.md)) guide. The current step I am on is getting my adapter from Managed mode to Master mode. The exact adapter I am using is the ALFA USB WiFi AWUS036NHA with the well-supported Atheros AR9271 chipset.

Every guide I have worked with is incredibly outdate telling me to use things like Madwifi which was legacy'd in 2008. I am not sure if using Madwifi is still something that I should use, I have tried installing ath9k_htc driver, but also run into issues with the instructions they provide (wanting me to using Jessie).

I am running Ubuntu 16.04.
[B]
lsusb
[/B]```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b531 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 005: ID 056a:5044 Wacom Co., Ltd 
**Bus 001 Device 006: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**iwconfig (cut)**
```

wlx00c0ca981089  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


```

**ifconfig**
```

wlx00c0ca981089 Link encap:Ethernet  HWaddr 00:c0:ca:98:10:89  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by chili555 on 2019-09-05
What is the result of:```
sudo service network-manager stop
sudo ip link set wlx00c0ca981089 down
sudo iwconfig wlx00c0ca981089 mode master
sudo ip link set wlx00c0ca981089 up
iwconfig
```

---

### Post by mnewber1 on 2019-09-06
> **chili555 said:**
> What is the result of:```
sudo service network-manager stop
sudo ip link set wlx00c0ca981089 down
sudo iwconfig wlx00c0ca981089 mode master
sudo ip link set wlx00c0ca981089 up
iwconfig
```

I get the following error when I do the command **sudo iwconfig wlx00c0ca981089 mode master**:

```

Error for wireless request "Set Mode" (8B06):
    SET failed on device wlx00c0ca981089 ; Invalid argument.

```

---

### Post by kevdog on 2019-09-07
Can your chipset actually be placed into master mode? Not all chipsets can.  You might have to research this.

---

