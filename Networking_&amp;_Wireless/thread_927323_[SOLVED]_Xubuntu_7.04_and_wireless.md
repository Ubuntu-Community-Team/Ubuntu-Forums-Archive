---
title: "[SOLVED] Xubuntu 7.04 and wireless??"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by Grone1985 on 2008-09-22
Hi,
I just installed Xubuntu 7.04 on this old HP laptop, and need to find a way to install the wireless and then configure it for WPA. I tried looking for some tutorials with wpa_supplicant but couldn't get it to work... Some info:

When i run *lspci* i get:
Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
I currently have internet access through LAN cable, and the device its using is eth0.

Any help will be really appreciated... Thanks in advance!!

---

### Post by nixscripter on 2008-09-23
Do you have the driver installed? ```
lshw -C network
```

If not, you can get the driver here (I think): [http://downloadcenter.intel.com/T8Clearance.aspx?url=/11780/eng/ipw2200_linux_1_2_0.tgz&agr=Y&ProductID=1637&DwnldID=11780&lang=eng](http://downloadcenter.intel.com/T8Clearance.aspx?url=/11780/eng/ipw2200_linux_1_2_0.tgz&agr=Y&ProductID=1637&DwnldID=11780&lang=eng)

---

### Post by willca on 2008-09-24
First of all lets verify if you wifi is even working before proceeding with the next steps as outlined.

sudo iwlist wlan0 scan

If at this point it sees other wireless networks, then great!

So now if you want to use WPA which is better than WEP here is how I go about this. It does not matter if its Gutsy or Hardy or Debian Etch or something. This works across Debian derivatives.

sudo apt-get install wpasupplicant (of course we need this)

Edit /etc/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
network={
ssid="YourWiFiSSID"
psk="YourWiFiPassword"
key_mgmt=WPA-PSK
proto=WPA
pairwise=TKIP
}

Test if its working....

sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

If it does then move onto the next.

Edit /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant


Then /etc/init.d/networking restart

---

### Post by Grone1985 on 2008-09-24
> **nixscripter said:**
> Do you have the driver installed? ```
lshw -C network
```

If not, you can get the driver here (I think): [http://downloadcenter.intel.com/T8Clearance.aspx?url=/11780/eng/ipw2200_linux_1_2_0.tgz&agr=Y&ProductID=1637&DwnldID=11780&lang=eng](http://downloadcenter.intel.com/T8Clearance.aspx?url=/11780/eng/ipw2200_linux_1_2_0.tgz&agr=Y&ProductID=1637&DwnldID=11780&lang=eng)

This is what I got from that command

```
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@02:04.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:5b:fe:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: iomemory:d0000000-d0000fff irq:22
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5705M_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@02:0e.0
       logical name: eth0
       version: 03
       serial: 00:12:79:c6:a9:5f
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.72 firmware=5705-v3.24 ip=192.168.2.7 latency=64 mingnt=64 multicast=yes
       resources: iomemory:d0020000-d002ffff irq:16
```

---

### Post by Grone1985 on 2008-09-24
> **willca said:**
> First of all lets verify if you wifi is even working before proceeding with the next steps as outlined.

sudo iwlist wlan0 scan


I got this:

```
wlan0     Interface doesn't support scanning.
```

I just figured that my wireless for some reason is named eth1 and not wlan0... and to that command it shows me...



```
eth1      Scan completed :
          Cell 01 - Address: 00:17:3F:66:17:08
                    ESSID:"RUBCAS"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-34 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 12ms ago
```

So should I do the same thing you said but with eth1 instead of wlan0?

---

### Post by nixscripter on 2008-09-25
Right. I wish there were a more standard naming system for interfaces.

---

### Post by Grone1985 on 2008-09-26
Yes, it would make it easier for some cases.
BTW thanks both of you... Got it working perfectly!

---

