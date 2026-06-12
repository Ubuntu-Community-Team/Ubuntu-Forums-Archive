---
title: "Wifi problems driving me crazy"
date: 2013-10-17
forum: Networking &amp; Wireless
---

### Post by adidasalley on 2013-10-17
I have a dell vostro 1500. it has a broadcom bcm 4311 wireless card. if i do a fresh ubuntu 12.04 install and run this 
"sudo apt-get purge b43-fwcutter firmware-b43-installer firmware-b43-lpphy-installer firmware-b43legacy-installer bcmwl*
sudo apt-get install b43-fwcutter firmware-b43-installer bcmwl*" then  the wireless will work just fine but as soon as i shut down the laptop and boot back up it will not find any wifi signal. please help it is very frustrating to have thought you figured it out then its gone on reboot. thanks

---

### Post by chili555 on 2013-10-17
Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot and tell us if it's working as expected.

---

### Post by adidasalley on 2013-10-17
computer works but wifi doesn't.  The light on the side of the computer for wifi isnt lit up either

---

### Post by chili555 on 2013-10-17
Please show us:```
lsmod | grep -e b43 -e wl
dmesg | grep b43
rfkill list all
```

---

### Post by adidasalley on 2013-10-17
mine@mine-vostro-1500:~$ lsmod | grep -e b43 -e wl
b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453919  2 b43,mac80211
bcma                   39810  1 b43
ssb                    51554  3 b43,ssb_hcd,b44
mine@mine-vostro-1500:~$ dmesg | grep b43
[   10.940272] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   10.984059] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   11.021191] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   11.021202] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   11.021209] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

---

### Post by chili555 on 2013-10-17
Please get a temporary ethernet connection and try:```
sudo apt-get install linux-firmware-nonfree
```Reboot and let us hear your report.

---

### Post by adidasalley on 2013-10-17
the wifi light is now on but it is not finding any connections. It never even searched. like when the lines scroll through the triangle when it is connecting.

---

### Post by chili555 on 2013-10-17
Did you detach the ethernet? Network Manager will prefer ethernet if it's available. How about:```
rfkill list all
sudo iwlist wlan0 scan
```if it scans, it should connect.

---

### Post by adidasalley on 2013-10-17
it is working after another reboot. it takes awhile to try and connect and i was impatient. thank you so much.

---

### Post by chili555 on 2013-10-17
Happy to hear it's working. Have fun!

---

