---
title: "Acer TM 4750g Wifi Atheros AR9287 not working"
date: 2019-03-02
forum: Networking &amp; Wireless
---

### Post by makacworker on 2019-03-02
Hallo I installed Ubuntu 1710 ti my Acer TravelMate 4750G with WiFi Atheros AR9287, wired network connection works right way, but WiFi is not working.
I am new user, can anybody help?
I tried rf kill list so result is:
```
kuldab@kuldab-TM4750:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
5: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

---

### Post by makacworker on 2019-03-02
```
kuldab@kuldab-TM4750:~$ sudo lshw -C network
[sudo] password for kuldab: 
  *-network DISABLED        
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 01
       serial: ec:55:f9:4e:ab:4e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.13.0-16-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d3200000-d320ffff
  *-network
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0f0
       version: 10
       serial: 20:6a:8a:3a:a1:d0
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=sb ip=192.168.0.232 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:d3100000-d310ffff memory:d3110000-d311ffff memory:d3400000-d34007ff
```

---

### Post by chili555 on 2019-03-02
> 5: phy1: Wireless LAN
Soft blocked: no
Hard blocked: [COLOR="#FF0000"]yes[/COLOR]Please find and press the wifi button, sometimes referred to as Airplane Mode.

Also, please run and post:```
lsmod | grep acer
```

---

### Post by makacworker on 2019-03-02
In case of my computer Wifi button is Fn key+ F3 it is switching Airplane mode Off/On it works now Airplane mode is Off

```
root@kuldab-TM4750:/home/kuldab# lsmod | grep acer
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
wmi                    24576  4 wmi_bmof,acer_wmi,mxm_wmi,nouveau
video                  40960  2 acer_wmi,nouveau
root@kuldab-TM4750:/home/kuldab#
```

---

### Post by makacworker on 2019-03-02
```
root@kuldab-TM4750:/home/kuldab# rfkill unblock all 
root@kuldab-TM4750:/home/kuldab# rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
7: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

---

### Post by chili555 on 2019-03-02
Please try an experiment:```
sudo modprobe -r acer-wmi
sudo rfkill unblock all
sudo rfkill list all
```

---

### Post by makacworker on 2019-03-02
chilli555 thank You for support, there is a result:
```
root@kuldab-TM4750:/home/kuldab# sudo modprobe -r acer-wmi
root@kuldab-TM4750:/home/kuldab# sudo rfkill unblock all
root@kuldab-TM4750:/home/kuldab# sudo rfkill list all
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
7: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@kuldab-TM4750:/home/kuldab#
```

---

### Post by chili555 on 2019-03-02
With *acer-wmi* unloaded, does the Airplane Mode switch have any effect? Please press it and check again:```
rfkill list all
```

---

### Post by coffeecat on 2019-03-02
> **makacworker said:**
> Hallo I installed Ubuntu 1710

If you mean Ubuntu 17.10, that has been end of life since July of last year. If this is a new installation, why did you install an obsolete and unsupported version?

---

### Post by makacworker on 2019-03-02
What does mean "with acer-wmi unloaded"?

```
kuldab@kuldab-TM4750:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

now I pushed Fn+F3 airplane mode was enabled, but no change in rfkill list about Wifi. There is change about Bluetooth

```
kuldab@kuldab-TM4750:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
5: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
kuldab@kuldab-TM4750:~$
```

---

### Post by makacworker on 2019-03-02
> **coffeecat said:**
> If you mean Ubuntu 17.10, that has been end of life since July of last year. If this is a new installation, why did you install an obsolete and unsupported version?

I tested Xubuntu 18.04 and there was same problem like now in Ubuntu 17.10 version. After problem will be fixed I can update to actual version.
So I have slow connection and I would like to do it when problem will be fixed.
I hope You understand me reason.

---

### Post by DuckHook on 2019-03-02
@OP

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by chili555 on 2019-03-02
Do you have this switch #3? What is its position?

[IMG]https://i.postimg.cc/KzXJyPxt/Screenshot-from-2019-03-02-16-37-13.png[/IMG]

---

### Post by chili555 on 2019-03-02
What is the position of button #3 as I requested above?

---

### Post by makacworker on 2019-03-03
I'm really ashamed of my incomprehension. Yes WiFi was switched Off by the switch #3.
Thank You and I am really sorry to wasting Your time to solve this stupid issue.

---

### Post by chili555 on 2019-03-03
I’m glad it’s working by whatever means. Have fun.

---

