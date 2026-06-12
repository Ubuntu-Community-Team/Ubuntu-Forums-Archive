---
title: "USB linksys stick no connecton on boot"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by Cyril_Grey on 2008-11-10
When I boot up wicd cant see my network. I can remove my usb wireless stick and put it back in and wicd will pick up my network and connect most of the time. The chipset is a prism 2


Dmesg is showing the default old driver being loaded during boot:

[   40.006714] prism2usb_init: prism2_usb.o: 0.2.8 Loaded
[   40.006716] prism2usb_init: dev_info is: prism2_usb
[   42.196186] ident: nic h/w: id=0x8026 1.0.0
[   42.198181] ident: pri f/w: id=0x15 1.1.2
[   42.200177] ident: sta f/w: id=0x1f 1.5.6
[   42.202173] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
[   42.204169] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
[   42.206165] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
[   42.208162] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/10
[   42.210157] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[   42.212153] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[   42.214151] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
[   42.216146] Prism2 card SN: 000000000000
[   42.224140] usbcore: registered new interface driver prism2_usb


Then Ndiswrapper comes along and loads another one:

[   44.808034] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   44.847620] Linux agpgart interface v0.102
[   44.995240] usbcore: registered new interface driver ndiswrapper


Right after this driver swap, udev switches the interface name:

[   44.997967] udev: renamed network interface wlan0 to wlan1

Now when I pop the usb device in and out the network comes up listed on wlan0

Looking at the udev persistent rules shows this:

# USB device 0x066b:0x2213 (prism2_usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:06:25:23:74:e7", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


Interfaces file :


auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp



iface wlan0 inet dhcp
wireless-essid ******
wireless-key **********



auto wlan0

#iface wlan1 inet dhcp

#auto wlan1

I am not familiar with linux enough to solve this but I get the feeling I am looking in the right direction. I am almost positive that I had this system connecting at boot before I upgraded to Hardy.

Any ideas?

---

### Post by dmizer on 2008-11-11
Do you still have NetworkManager enabled? If so, please disable it according to these directions: [https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)

---

### Post by Cyril_Grey on 2008-11-11
Thanks for the feedback dmizer

I dont believe NetworkManager is enabled or even still present on this system. Wicd removes these packages on installation as far as I know.

---

### Post by dmizer on 2008-11-11
> **Cyril_Grey said:**
> Thanks for the feedback dmizer

I dont believe NetworkManager is enabled or even still present on this system. Wicd removes these packages on installation as far as I know.

You'd be surprised. Double check with this command:
```
ps aux | grep nm-applet
```

---

### Post by Cyril_Grey on 2008-11-11
Code returns the following:


seth@linux:~$ ps aux | grep nm-applet
seth     10293  0.0  0.0   3004   764 pts/0    S+   19:22   0:00 grep nm-applet

---

### Post by Cyril_Grey on 2008-11-11
I can see Network Manager in the Sessions preferences :/ It is present and enabled.

---

### Post by Cyril_Grey on 2008-11-11
I have the connection working at boot now by uncommenting the wlan1 interface and configuring it with the proper essid and key.

Wicd No longer works since it is looking for the wlan0 interface. I changed this setting in wicd and it sees the network and connects however then the connection does not come up on the next boot, or it does then wicd proceeds to kill it.

Either way I am connecting on boot now so thanks Dmizer

---

