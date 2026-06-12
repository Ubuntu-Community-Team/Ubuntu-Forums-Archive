---
title: "[SOLVED] Error when trying to get up my wlan0 interface"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by Telémakhos on 2008-10-30
This is the device:

> loyx@Apollo:~$ lsusb | grep Wireless
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter


My interfaces:

> loyx@Apollo:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


This is what I've in /etc/network/interfaces

> auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.0.30
netmask 255.255.255.0
gateway 192.168.0.1

iface eth1 inet dhcp
address 192.168.0.30
netmask 255.255.255.0
gateway 192.168.0.1

#auto eth1

auto eth1


And this is the error:

> loyx@Apollo:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device




My RTL8187 works out of the box with network-manager. After install/uninstall wifi-radar and ndiswrapper is messed... Anyone can point me in the good direction to get it working?

Thanks a lot

---

### Post by Ayuthia on 2008-10-30
Can you post the results of:
```
lsmod |grep -e 8187 -e ndis
```
It might be a matter of blacklisting ndiswrapper and adding rtl8187 to /etc/modules.

---

### Post by Telémakhos on 2008-10-30
Here's the result:

> loyx@Apollo:~$ lsmod |grep -e 8187 -e ndis
ndiswrapper           196380  0 
usbcore               148848  5 ndiswrapper,usbhid,uhci_hcd,ehci_hcd


---

### Post by Ayuthia on 2008-10-30
> **Telémakhos said:**
> Here's the result:

You might try:
```
sudo modprobe -r ndiswrapper
sudo modprobe rtl8187
sudo /etc/init.d/restart
sudo iwlist scan
```

---

### Post by Telémakhos on 2008-10-30
Solved!!! :D

Thank you soooo much Ayuthia ;)

---

