---
title: "Belkin Wireless USB Dongle That Works Out-of-the-Box"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by Jæd on 2007-11-16
Hi,

Just to let people know the following USB Dongle Works Out-of-the-box on Gutsy.

[http://www.aria.co.uk/Products/Peripherals/Network+Products/Adapter/Wireless-G+%2854Mbps%29/Belkin+Wireless+USB+Network+Adapter+802.11g?productId=27747]("http://www.aria.co.uk/Products/Peripherals/Network+Products/Adapter/Wireless-G+%2854Mbps%29/Belkin+Wireless+USB+Network+Adapter+802.11g?productId=27747")

Its also quite cheap...! So far I haven't had any dropped connections. 

To get it working I had to manually fill in my WEP key + network name, and then did:


```

sudo ifdown wlan0
sudo ifup wlan0

```
Disclaimer: I don't work for Aria, just a happy customer...

---

### Post by rustybronco on 2007-11-16
you can add to the list at  [http://ubuntuhcl.org/pub/](http://ubuntuhcl.org/pub/)
and here [http://ubuntuforums.org/showthread.php?t=361236](http://ubuntuforums.org/showthread.php?t=361236)

---

