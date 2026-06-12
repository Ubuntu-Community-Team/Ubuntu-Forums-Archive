---
title: "Issue with Wifi on HP Pavilion dv6000 laptop after installing Ubuntu 18.04"
date: 2021-03-10
forum: Networking &amp; Wireless
---

### Post by agnelocorrea on 2021-03-10
Hello,
I am new to Ubuntu and have this issue with my Wifi on my HP Pavilion dv6000 laptop. I have installed Ubuntu 18.0.4.5 LTS.

[COLOR=#000000]```
[/COLOR]
$lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 18.04.5 LTS
Release: 18.04
Codename: bionic
[COLOR=#000000]
```
[/COLOR]
The wifi works fine and I am able to connect to the network with no issues accessing the internet. I can also view other networks and can connect. After 3 - 4 hrs or probably once the laptop goes into standby (not sure), the wifi shows connected but I have no internet access. From the GUI, I tried to connect to another network but am unable to see any networks. I disconnected the present network which says connected and once this is done I am unable to see even the network I had connected. There are no wifi networks displayed. Once I restart the laptop I am able to connect to wifi and the internet works fine till such a time the same cycle follows and again I am unable to access the internet. Every time I face the issue I have to restart my laptop. I have tried to restart the network manager without any success.
sudo service network-manager restart

Below is the output of sudo lshw -class network:
I can see that the wireless interface has network Disabled. The only solution I have at the moment is to restart the laptop and it works fine but I don't think this is the correct solution. Not sure if its an issue with the driver. Can someone help???

```

:~$ sudo lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:76:bc:d9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=4.15.0-136-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:26 memory:d6000000-d6000fff
  
*-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:af:75:dd
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)

```

I have tried to enable the WiFi using GUI or CLI but it does not get enabled. Rebooting the laptop is the only option.

I have tried all these but still no success
Using systemctl
sudo systemctl restart NetworkManager.service

using nmcli
$ sudo nmcli networking off
$ sudo nmcli networking on

$ sudo ifdown -a
$ sudo ifup -a

---

### Post by coffeecat on 2021-03-10
Welcome to the forum.

I've edited your post to restore default font properties and to add BBCode code tags. The font and colour you chose were difficult to read - please always use default font/size/colour unless you wish to highlight something. There's no need for text formatting when using default font properties. Also, I've added code tags to your terminal output in order to restore vertical columns. Please always use code tags when posting terminal output or for the contents of configuration files. There's a link in my sig that explains how to use code tags.

Good luck.

---

### Post by agnelocorrea on 2021-03-10
I restarted the laptop and the wlan0 is enabled. Bust after the laptop goes into idle mode i think the wifi adapter gets disabled and cannot be enabled unless the laptop is restarted.
[COLOR=#000000]```
[/COLOR]
sudo lshw -C network                                                                                           
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:76:bc:d9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wir                                                                                        eless
       configuration: broadcast=yes driver=iwl3945 driverversion=4.15.0-136-gene                                                                                        ric firmware=15.32.2.9 ip=192.168.3.185 latency=0 link=yes multicast=yes wireles                                                                                        s=IEEE 802.11
       resources: irq:25 memory:d6000000-d6000fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:af:75:dd
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-f                                                                                        d 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion                                                                                        =3.5.24-k2-NAPI duplex=half latency=64 link=no maxlatency=56 mingnt=8 multicast=                                                                                        yes port=MII speed=10Mbit/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)

 
iwconfig
 lo        no wireless extensions.
 
wlan0     IEEE 802.11  ESSID:"TALKTALK0E69AD_5G"
          Mode:Managed  Frequency:5.18 GHz  Access Point: 30:AA:E4:E7:75:C8
          Bit Rate=48 Mb/s   Tx-Power=14 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=60/70  Signal level=-50 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:87   Missed beacon:0
 
eth0      no wireless extensions.
[COLOR=#000000]
```[/COLOR]

---

### Post by agnelocorrea on 2021-03-10
Just to keep everyone updated.

I could see from running command $iwconfig, the Power Management was ON

```

$iwconfig

wlan0     IEEE 802.11  ESSID:"TALKTALK0E69AD_5G"
          Mode:Managed  Frequency:5.18 GHz  Access Point: 30:AA:E4:E7:75:C8
          Bit Rate=48 Mb/s   Tx-Power=14 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=60/70  Signal level=-50 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:87   Missed beacon:0

```

I accessed default-wifi-powersave-on.conf in /etc/NetworkManager/conf.d and edited this file to change the value from 3 to 2

```


$sudo nano default-wifi-powersave-on.conf

wifi.powersave=2


```

now run the following command

```

$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11  ESSID:"TALKTALK0E69AD_5G"
          Mode:Managed  Frequency:5.18 GHz  Access Point: 30:AA:E4:E7:75:C8
          Bit Rate=48 Mb/s   Tx-Power=14 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:276   Missed beacon:0

```


The power management should be off. Hope this resolves the issue.

---

