---
title: "Problem with 14.04 LTS and NetGear WNA1000M"
date: 2014-11-04
forum: Networking &amp; Wireless
---

### Post by Rishin_Goswami on 2014-11-04
I have a fairly weird problem where my internet seems to stop working 5 minutes after boot up - Pinging to the default gateway also fails (Router is still up and working). The network adapter is still up and WiFi is still connected. I have tried multiple clients, so I would rule out a pure software issue. And things just work fine on windows, so I would rule out a hardware issue. The system I'm running is:


```
Linux mysys 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```


The WiFi adapter details from `lsusb`:


```
Bus 002 Device 003: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
```


Results of `lsmod | grep rtl`:


```

rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              630653  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              484040  2 mac80211,rtlwifi

```




I see that the driver loaded is slightly different from the USB one - Is that it? If so, how to fix it?


Any ideas are appreciated.

---

### Post by chili555 on 2014-11-04
> I see that the driver loaded is slightly different from the USB one - Is that it? If so, how to fix it?No fix is needed. Someone at the Realtek factory hard-codes a series into the silicone. The Linux developer named the driver under the 8192 umbrella with the 'cu' suffix. There is no problem whatever in that regard.

The driver instability is, of course, another question. There is a well-known bug in the driver. I believe you can fix it.  Disconnect your wireless connection (unplug the USB adapter that contains the Realtek chipset), and temporarily connect to the internet by means of an ethernet cable (or by means of another wireless chipset that does function well).

Now install some applications for building the right driver via a terminal:
```
sudo apt-get install linux-headers-generic build-essential dkms git
```

Now download the source code of the driver via a terminal:
```
git clone https://github.com/pvaret/rtl8192cu-fixes.git
```

Set it up as a DKMS module via a terminal:
```
sudo dkms add ./rtl8192cu-fixes
```

Build and install the new driver via a terminal:
```
sudo dkms install 8192cu/1.9
```

Refresh the module list via a terminal:
```
sudo depmod -a
```

Blacklist the faulty driver via a terminal:
```
sudo -i
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit
```

Detach the ethernet and reboot; the wireless should be working much better now.

Note: a possibly surprising side effect might be, that the light on your wireless card is blinking constantly now. That's normal: the light is blinking whenever data are being sent or received.

---

### Post by Rishin_Goswami on 2014-11-15
Thanks. Works perfectly.

---

### Post by Entheo on 2014-12-10
I have been struggling with the same problem as OP and have tried lots of different ways but no joy. 

Chili you are awesome! It has worked for me on xubuntu 14.04 and i now have wifi on my pc.

Thanks fella ;)

---

