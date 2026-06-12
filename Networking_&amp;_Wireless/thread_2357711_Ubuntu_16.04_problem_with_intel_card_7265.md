---
title: "Ubuntu 16.04 problem with intel card 7265"
date: 2017-04-05
forum: Networking &amp; Wireless
---

### Post by peppe-is on 2017-04-05
[COLOR=#000080]Hi guys, in my laptop wireless card don't work. I have ubuntu 16.04 and windows 10, but in windows there aren't problems. [/COLOR]
```
rfkill list
```
```
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

after ```
rfkill unblock all
```
```
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

```
iwconfig
```
```
enp2s0    no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.


```

```
sudo lshw -c network
```
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: 70:8b:cd:8e:88:4b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.1.8 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:127 ioport:d000(size=256) memory:df204000-df204fff memory:df200000-df203fff
  *-network DISABLED
       description: Wireless interface
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 59
       serial: 7c:b0:c2:4a:f4:61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.8.0-46-generic firmware=22.361476.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:131 memory:df100000-df101fff

```

```
lspci -nn | grep -i net
```
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
03:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)

```


[COLOR=#000080]help me please, I tried all[/COLOR]

---

### Post by howefield on 2017-04-05
Hello and welcome to the forums, despite being a piece of Hardware I have moved your thread to the "*Networking & Wireless*" forum which is probably a better fit.

---

### Post by peppe-is on 2017-04-05
Thanks and excuse my ignorance. I hope someone help me to solve.

---

### Post by jeremy31 on 2017-04-05
You should try ```
echo "options asus-nb-wmi wapf=4" | sudo tee /etc/modprobe.d/asus-nb-wmi.conf
```
Reboot

---

### Post by peppe-is on 2017-04-05
[COLOR=#000080][B][SIZE=3]Thank you so much =d>=d>=d>, after the steps 
[/SIZE][/B][/COLOR]>  ```
 echo "options asus-nb-wmi wapf=4" | sudo tee /etc/modprobe.d/asus-nb-wmi.conf 

```
Reboot [COLOR=#000080][B][SIZE=3]
wireless card work very well. 
[/SIZE][/B][/COLOR][SIZE=2]```
rfkill list
```
```
1: phy0: Wireless LAN
    Soft blocked: no
    [COLOR=#ff0000]Hard blocked: no[/COLOR]
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```.

[/SIZE]

---

