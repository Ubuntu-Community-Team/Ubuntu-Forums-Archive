---
title: "Wifi Disable by Hardware Switch | HP-pavilion-11-x360 |Ralink corp. RT3290 LE"
date: 2019-03-21
forum: Networking &amp; Wireless
---

### Post by anartificialme on 2019-03-21
Hola Everyone
m a newbie in Linux world, and this WiFi error stuff keep bugging me. i did boot from Windows 10, and everything fine. here's output from Wireless Script.

```


[https://paste.ubuntu.com/p/DfRrXZrWVS/](https://paste.ubuntu.com/p/DfRrXZrWVS/)

```

any suggestion?

---

### Post by praseodym on 2019-03-21
Lets try
```

sudo modprobe -rfv rt2800pci
sudo rfkill unblock all
sudo modprobe -v rt2800pci
rfkill list
iwconfig
```
Otherwise: Any button, switch, key or key combo?

---

### Post by anartificialme on 2019-03-21
> **praseodym said:**
> Lets try
```

sudo modprobe -rfv rt2800pci
sudo rfkill unblock all
sudo modprobe -v rt2800pci
rfkill list
iwconfig
```
Otherwise: Any button, switch, key or key combo? 

thanks a lot mate, but seem it still need to tweak lil bit

rfkill list
```
0: phy0: Wireless LAN    Soft blocked: no
    Hard blocked: yes



```

iwconfig

```
enp4s0    no wireless extensions.

wlp2s0f0  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:off
          
enp0s20u2  no wireless extensions.


lo        no wireless extensions.



```

for wireless button, i pressed as manual said, and nothing happen :(

lshw -C network

```
 *-network DISABLED               description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0f0
       version: 00
       serial: 38:b1:db:17:d9:51
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=5.0.0-050000-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:90710000-9071ffff



```

---

### Post by praseodym on 2019-03-22
Lets try
```

sudo rmmod hp_wmi
rfkill unblock all
```

---

### Post by anartificialme on 2019-03-22
> **praseodym said:**
> Lets try
```

sudo rmmod hp_wmi
rfkill unblock all
```

Nothing Happen Mate, :( :(

---

### Post by praseodym on 2019-03-23
Try

[LIST]
[*]Pressing the button/switch permanently during boot-up
[*]Pressing it repeatedly during boot-up
[*]Switch in "On" Position during boot-up
[/LIST]

---

### Post by anartificialme on 2019-03-23
> **praseodym said:**
> Try

[LIST]
[*]Pressing the button/switch permanently during boot-up
[*]Pressing it repeatedly during boot-up
[*]Switch in "On" Position during boot-up
[/LIST]

 
Same, it's persist. how about if i uninstall RT2800pci driver?is it doable?

---

### Post by praseodym on 2019-03-23
Yes, try this one instead
```

sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/06/23/5641297-RT3290_u16_v3.tar.gz
tar xvf 5641297-RT3290_u16_v3.tar.gz
cd RT3290_u16
tar xvf src.tar.gz
./compile.sh
sudo ./install.sh
sudo cp firmware/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf  
```
Reboot

---

### Post by gokulmettur on 2020-02-14
The mentioned code(from _[https://media-cdn.ubuntu-de.org/forum/attachments/06/23/5641297-RT3290_u16_v3.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/06/23/5641297-RT3290_u16_v3.tar.gz)_ ) inside the downloaded folder gives compilation errors at sta_ioctl.c during the function call **[FONT=courier new]access_ok[/FONT]**

---

