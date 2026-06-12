---
title: "Unable to activate wlan interface"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by TeeLicht on 2006-07-24
Hi folks!

I'm using a Linksys pcmcia-card with a broadcom chipset. I managed to activate it by using ndiswrapper (hardware present, driver present). Surprisingly my wireless device gets detected as eth1. If I want to activate it in the network settings, I get an error message.

iwconfig gives me the following output:
```
eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Thomas

---

### Post by beemer on 2006-07-24
I had the same issue with my Linksys USB adapter (WUSB54Gv1).  using the lsmod command, I found there was another driver trying to use my device at the same time ndiswrapper was.

This resulted in my adapter listing as eth1 and the only command I could issue was for setting the essid.

If you can find the other driver name (mine was islsm_usb, others on the web I've seen were islsm_pci) you can edit the file /etc/modprobe.d/blacklist (or add it if necessary) and add a line like:

blacklist drivername

(i.e. mine was "blacklist islsm_usb")

After that (and a reboot), the bad driver didn't load and ndiswrapper was able to properly do it's job.

Beemer

---

### Post by TeeLicht on 2006-07-24
Thank you for your answer. Anybody any ideas how to find this driver?

---

### Post by beemer on 2006-07-24
from a command prompt:

lsmod

look for anything that appears to be attached to your pcmcia card.

You can try:

lsmod | grep pcmcia

And that *might* narrow down the list.  Hopefully, if this is right, you'll see several lines and one has ndiswrapper *and* a couple others.  You can google the 'couple others' to see if one of them is actually a linux driver.  That'll be the one you want to try blacklisting.

Beemer

---

