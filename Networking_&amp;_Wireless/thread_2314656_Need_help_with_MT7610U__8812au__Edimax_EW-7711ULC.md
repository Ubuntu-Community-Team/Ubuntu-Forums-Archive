---
title: "Need help with MT7610U / 8812au / Edimax EW-7711ULC"
date: 2016-02-22
forum: Networking &amp; Wireless
---

### Post by billvh375 on 2016-02-22
Hi, I'm totally new here.  I have spent 6 hours today trying every combination I could find online to build the linux driver for this wi-fi USB device.  I tried chili555's 5 minute and 5 day options ;-)  I've run "make clean" "make" "sudo make install" "modprobe 8812au" more times than I can count.  I have tried various git repos with instructions.  But nothing lights up the USB wi-fi adapter.

iwconfig gives:
eth0      no wireless extensions.
eth1      no wireless extensions.
ra0       Ralink STA  
lo        no wireless extensions.

When the USB device is plugged in, but ifconfig gives only eth0, eth1, and lo when the device is plugged in or not.  I can't get wlan0 to show up.  I feel I'm unsuccessfully building a driver for this device, but I don't know what to try next.  Is anyone willing to walk me through this configuration?

Thanks in advance for any help anyone can provide.

billvh375

---

### Post by chili555 on 2016-02-23
mt7610u is for a few Ralink devices; 8812au is for some Realtek devices. Your device is one or the other; not both! Of course, it is also possible that it is neither!

Let's start by identifying the exact device. Please run and post, with the device inserted:```
lsusb
```

---

