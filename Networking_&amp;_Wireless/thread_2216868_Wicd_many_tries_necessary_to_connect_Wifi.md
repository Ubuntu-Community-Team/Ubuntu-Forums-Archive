---
title: "Wicd many tries necessary to connect Wifi"
date: 2014-04-14
forum: Networking &amp; Wireless
---

### Post by Raph_B on 2014-04-14
Hi,

Since few months , I have difficulty to connect to a network with a quasi-perfest signal (less then 90%).  
I need many tries before finally be able to have a connection, Wicd saying ... Connection Failed : Bad Password (the password is good)
I'm using Wicd because, It's a little bit faster to connect... 
On Window , there is no problem...
I re-installed Ubuntu 12.10 32 bit LTS , but the problem is still there. And like I said , the problem appeared few months ago ...
And It's a public router , I cannot play with it.

Thank for the help!

iwconfig

```
 iwconfigwlan0     IEEE 802.11bg  ESSID:"UQAM Wi-Fi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:3A:98:0A:49:02   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:435   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.



```

ifconfig
```
ifconfigeth0      Link encap:Ethernet  HWaddr e8:e0:b7:47:8d:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:e0600000-e0620000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:274474 (274.4 KB)  TX bytes:274474 (274.4 KB)


wlan0     Link encap:Ethernet  HWaddr 68:5d:43:b3:35:58  
          inet addr:172.29.126.188  Bcast:172.29.127.255  Mask:255.255.192.0
          inet6 addr: fe80::6a5d:43ff:feb3:3558/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13442553 (13.4 MB)  TX bytes:2836435 (2.8 MB)



```

iwlist
```
iwlist scanw
lan0     Scan completed :
          Cell 01 - Address: 00:3A:98:0A:49:02
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"UQAM Wi-Fi"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d4d30614d
                    Extra: Last beacon: 464348ms ago
                    IE: Unknown: 000A5551414D2057692D4669
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B0516001C8D5B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3202606C
                    IE: Unknown: 851E01008F000F00FF035900504B2D31412D4150320000000000000016000027
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.



```


 sudo lshw -C network
```
 *-network                      description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: e8:e0:b7:47:8d:62
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:e0600000-e061ffff memory:e063b000-e063bfff ioport:2080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: c4
       serial: 68:5d:43:b3:35:58
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-45-generic firmware=18.168.6.1 ip=172.29.126.188 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:45 memory:e0400000-e0401fff
```

---

### Post by praseodym on 2014-04-14
Which encryption mode do you use? Try this Add-On for Wicd:
```

wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
# Installation
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
It brings a lot of templates for mixed-mode, hidden networks, etc.

Additionally, you may want to deactivate the N-mode of the driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Did you choose **wlan0** as interface name and **wext** as driver in Wicd? Network-manager is deactivated or uninstalled?

---

### Post by Raph_B on 2014-04-14
Hi !
Thank for your answer !

I tried what you said , the problem is still here.

For your questions, I use many encryptions mode because I work in many places , home ,coffee , university .ect
The majority of time, it's WPA2
I use wlan0.

I tried both Network-manager desactived and uninstalled.

---

### Post by praseodym on 2014-04-14
I just saw you wrote 12.10! This one is outdated, therefore I recommend a fresh install of 12.04.4 LTS or 13.10 (or the beta of 14.04 LTS). But lets check first
```

lsb_release -a
sudo killall wpa_supplicant
sudo service wicd restart
ps aux | egrep '[N]etw|[W]icd|[W]pa'
```

---

### Post by Raph_B on 2014-04-14
Yeah I use 12.10 because a software I used work well on 12.10, anyway with 13.10 I got the same problem  (I was using 13.10 before)  ...
I will install 14.10 this week with the final release.

Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal


sudo killall wpa-supplicant
 
wpa-supplicant: no process found


sudo service wicd restart 
 * Restarting Network connection manager wicd                            [ OK ] 


ps aux | egrep '[N]etw|[W]icd|[W]pa'
root       916  0.0  0.0  25228  5476 ?        Ssl  13:39   0:01 NetworkManager

---

### Post by praseodym on 2014-04-14
Networkmanager is still running:
```

sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```

---

### Post by Raph_B on 2014-04-14
Yeap I know , I re-installed it this morning :), Just to compare. 

I did what you told me. I think the signal is stronger but I took me three tries to connect to the wifi ..

Again, thank for yelp!

---

