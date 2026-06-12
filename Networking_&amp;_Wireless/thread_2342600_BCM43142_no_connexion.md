---
title: "BCM43142 no connexion"
date: 2016-11-08
forum: Networking &amp; Wireless
---

### Post by christian-jamard on 2016-11-08
Hello,

I can't connect my laptop to wifi network : I see my wifi networks in network manager but nothing append when I key the connection pathword.

I tried, without improvement :
- sudo apt-get install --reinstall bcmwl-kernel-source
- sudo ifconfig wlo1 up
- secure boot is disabled.

```
etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
```

I tried to repalce wlan0 with wlo1 in interface and restart network manager.
Result : Wifi network had disappeared from network manager.

```
/etc/modprobe.d/blacklist.conf :
[...]
# replaced by b43 and ssb.
blacklist bcm43xx
[...]
```

```
iwconfig
lo        no wireless extensions.
wlo1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
eno1      no wireless extensions.
```

```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Thank you for your help.
Christian

---

### Post by jeremy31 on 2016-11-08
I would start by changing your /etc/network/interfaces to
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```
As you don't have a wlan0 interface, reboot

---

### Post by christian-jamard on 2016-11-08
With an interface like below, and reboot, nothing change.
```

etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
# auto wlan0
# iface wlan0 inet dhcp
```

---

### Post by jeremy31 on 2016-11-08
See the wireless script link in my signature and post the results

---

### Post by christian-jamard on 2016-11-08
Without response, I tried to fix the connexion by myself.
I managed to do it, thanks to your script.

I focused in wlo1, beginning wtih graphical network manager.
I had 2 choice for the device in the Wifi tab :
- an address like this XX:XX:XX:XX:XX:XX was selected
- wlo1 (XX:XX:XX:XX:XX:XX)
I selected the second choice and the connexion was fixed !

thank you

---

