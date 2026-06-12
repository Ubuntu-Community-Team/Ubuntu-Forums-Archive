---
title: "Intel 5100AGN: Disabled by hardware switch"
date: 2014-04-04
forum: Networking &amp; Wireless
---

### Post by phaerel on 2014-04-04
Hello,


I have problems regarding getting my WiFi Module of my Thinkpad (W500) to work.
The module is an Intel 5100AGN and the problem is that the NetworkManager tells me that my wireless device is "disabled by hardware switch".

Your first thought might well be that the actual radio switch is not on, but it is. I can see that because the Bluetooth connection works.
It is also (at least what I know) not disabled by any fn-key (as that would be an "disabled by software switch").

I also looked inside my laptop and tried looking if maybe the antenna cables are plugged out (I don't know if such an issue could cause one like I am having one),
but the white (Main) and black (AUX) antenna cables are all plugged in correctly, just like the manual from Intel states it.

Here is the output of "rfkill list":
```
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: hci0: Bluetooth
    Soft blocked: no
```

Thank you in advance for your help!


Greetings
phaerel

---

### Post by grahammechanical on 2014-04-04
> [COLOR=#000000]It is also (at least what I know) not disabled by any fn-key (as that would be an "disabled by software switch").[/COLOR]

I do not think that you are correct. Not being switched on by the Fn key combination would be considered as Hard Blocked. Is there another OS on that machine? It used to be, and for all I know it may still be true, that if we disable WiFi networking in Windows it then becomes very difficult to enable wireless in Linux. This command might help

```
rfkill unblock wifi
```

another two useful commands

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

We do them in that order. I also find these command useful

```
nm-tool
sudo lshw -C network
```

Regards.

---

### Post by phaerel on 2014-04-04
Hello,

No, there is only Ubuntu installed on that device.

```
rfkill unblock wifi
```

didn't help, and the ifconfig commands don't work because of "Operation not possible due to RF-kill".

nm-tool:
```

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        00:21:5D:8B:03:70

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
```

lshw:
```
*-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:8b:03:70
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-19-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:f4200000-f4201fff

```

---

