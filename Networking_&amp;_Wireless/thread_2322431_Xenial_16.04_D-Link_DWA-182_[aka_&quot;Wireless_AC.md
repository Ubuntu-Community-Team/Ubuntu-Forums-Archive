---
title: "Xenial 16.04: D-Link DWA-182 [aka &quot;Wireless AC1200 Dual Band USB Adapter&quot;]"
date: 2016-04-28
forum: Networking &amp; Wireless
---

### Post by felgro on 2016-04-28
Hello,

This is what I have, it's a gigabit wireless ethernet USB stick -

[http://us.dlink.com/products/connect/wireless-ac1200-dual-band-usb-adapter/](http://us.dlink.com/products/connect/wireless-ac1200-dual-band-usb-adapter/)

It's history is as follows -


[LIST]
[*]14.04 - working fine using this driver [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux) 
[*]Upgrade to 15.04 - broken, driver no longer working. Same with 15.10 - I assumed due to changes with systemd or something. Gave up trying. 
[*]Ran 16.04 LiveCD, plugged it in, instantly recognized, worked within seconds using only native Ubuntu. Heart fluttered with joy. 
[*]Intalled 16.04 - broken again 
[/LIST]

lsusb shows -

```
Bus 002 Device 002: ID 2001:3315 D-Link Corp.
```

Which is the correct identity for the device.

Now I don't want to install the rtl8812AU_8821AU_linux driver as I suspect it will have same problem as I had with 15.0x. Has anyone played with this device on 16.04 and can they offer any advice? Why did it work live, but not on install? That is the big question.

---

### Post by felgro on 2016-04-30
bump

---

### Post by chili555 on 2016-05-01
The driver makes for me with a couple of possibly harmless warnings using the process here in 16.04: [http://askubuntu.com/questions/573737/alfa-awus036ac-usb-wifi-adapter/573741#573741](http://askubuntu.com/questions/573737/alfa-awus036ac-usb-wifi-adapter/573741#573741)

The github repo has been updated a few times.> Why did it work live, but not on install? That is the big question. I have no idea. It shouldn't have. I would have bet a months paycheck that it wouldn't.

---

### Post by praseodym on 2016-05-01
Is the device ID part of that driver?
```

modprobe -c | grep -i "2001.*3315"
```

[http://packages.ubuntu.com/xenial/rtl8812au-dkms](http://packages.ubuntu.com/xenial/rtl8812au-dkms)

Edit: It is:

```
modprobe -c | grep -i "2001.*3315"
alias usb:v[COLOR="#FF0000"]2001[/COLOR]p[COLOR="#FF0000"]3315[/COLOR]d*dc*dsc*dp*ic*isc*ip*in* 8812au
```
Build with kernel 3.13-70 64bit under 14.04

---

### Post by chili555 on 2016-05-01
> **praseodym said:**
> Is the device ID part of that driver?
The driver I compiled as above says:```
chili@T440p:~/Desktop/Forum/rtl8812AU_8821AU_linux$ modinfo 8812au.ko | grep 3315
alias:          usb:v[COLOR="#FF0000"]2001[/COLOR]p[COLOR="#FF0000"]3315[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*

```

---

### Post by felgro on 2016-05-02
> **chili555 said:**
> The driver makes for me with a couple of possibly harmless warnings using the process here in 16.04: [http://askubuntu.com/questions/573737/alfa-awus036ac-usb-wifi-adapter/573741#573741](http://askubuntu.com/questions/573737/alfa-awus036ac-usb-wifi-adapter/573741#573741)

Yeah, I bet the bullet and installed that driver after seeing it was last revised a month ago. Now I have a fresh problem - the device can now connect, but only with WEP - I need to use WPA, and when I attempt to change it, the connect button is grayed out. The WEP connection can reach the internet, but not my other devices connected to the router. I don't need gigabit wireless for the 'net, but I do for my NAS, which is the main reason to use it.

Thoughts?

---

### Post by chili555 on 2016-05-02
I'd set the router to WPA2-AES, sometimes called, in routers, CCMP. Double-check the password. I do not recommend any auto WPA or WPA2 mode, or auto PSK or AES mode. I do not want my router to decide to switch to a *less* secure setting depending on whether the microwave is running or the moon is full. I only want the most secure setting it has, always.

I haven't the polite words to say how much I hate TKIP.

Most devices, 'Pods, 'Pads, phones, etc. that were made in the last 7-8 years will have no problem with WPA2-AES.

In my limited experience, the connect button is greyed out when Network Manager thinks the password doesn't have enough characters.

---

### Post by praseodym on 2016-05-02
Try starting the NM from terminal via
```

gksudo nm-connection-editor
```

---

### Post by felgro on 2016-05-15
[B]UPDATE -

[/B]To get device talking -

1. Absurdly obvious, therefore overlooked by all and me. Plug in device, goto Software and Updates, wait for it to detect D-Link and select following -

[IMG]http://i.imgur.com/70lKcUu.png[/IMG]

This allows device to be fully recognized, but still dead. So, next...

2. A suggestion at several forums though with no explanation of *why?* Get into BIOS and disable *'secure boot'*. Restart normally and the device is now visible, configurable and usable in *network manager* (sort of).

According to these outputs, 5GHz/1000mb should be now functional -

```
~$ iwconfig
enxc0a0bbe29477  IEEE 802.11AC  ESSID:"xxxxxxxxx"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:5.18 GHz  Access Point: 78:54:2E:4D:92:DE   
          Bit Rate:867 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=75/100  Signal level=57/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

~$ sudo lshw
*-usb:0
                      description: Generic USB device
                      product: D-Link Wireless Adapter
                      vendor: Realtek
                      physical id: 3
                      bus info: usb@1:1.3
                      version: 0.00
                      serial: 123456
                      capabilities: usb-2.00
                      configuration: driver=rtl8812au maxpower=500mA speed=480Mbit/s
```

It does function - but only on 2.4GHz/100mb, and then nowhere near the speed of the on board 100mb wireless adapter. Checking lsusb -

```
Bus 001 Device 008: ID 2001:3315 D-Link Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  ***bcdUSB               2.00***
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2001 D-Link Corp.
  idProduct          0x3315 
  bcdDevice            0.00
  iManufacturer           1 Realtek
  iProduct                2 D-Link Wireless Adapter
  iSerial                 3 123456
```

Does this imply USB 3.0 is no go? No matter, plugging into USB 2.0 port resolves nothing. As recommended before, security was forced to *WPA2 only/AES* - but *auto* and other variants also do nothing (I have avoided regressing to WEP) -

[IMG]http://i.imgur.com/GBdZq6V.png[/IMG]

Really at wit's end with this.

---

### Post by robert shearer on 2016-06-22
I have been following your progress and finally tried installing using the 'additional drivers'  you referenced.
Everything installed and after a reboot the adaptor is working. I have only tried it configured for 5Ghz and can report it works. My laptop has no usb3 port so I am using an express card usb3 adaptor.
From reading I believe I cannot get full usb3 speeds from it because of a limitation of the laptop chipset but it certainly performs faster for most usb communications than usb2 ports.

Attached is a screenshot from my Fritz!box monitoring showing the adaptors connection, reported and actual throughput.

One thing to bear in mind is that while the adaptor itself is usb3 capable the cradle that comes with it is not ! It is usb2!  If you're not already plugging the adaptor directly to a usb3 port try doing so.

---

