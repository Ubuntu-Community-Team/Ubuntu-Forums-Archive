---
title: "Ndiswrapper Wireless Present but not in ifconfig"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by jfanaian on 2007-02-13
I had my wireless working fine with ndiswrapper, until all of the sudden I boot today and they aren't working. I try doing iwconfig and the wlan0 device doesn't show up. I do ifconfig -a and its not there either. I try doing ndiswrapper -l and it shows the driver and hardware both present. They also show up in lsmod. I'm not sure what else to try. I have tried removing the drivers and adding them again in ndiswrapper but nothing. I can't get it to show up as a device in ifconfig or iwconfig.

Here is the output for lsmod:
```

# lsmod|grep ndiswrapper
ndiswrapper           204436  0 
usbcore               134912  4 ndiswrapper,ehci_hcd,ohci_hcd

```

Here is ndiswrapper -l
```

# ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

```

And lastly iwconfig:
```

# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

Thanks again :)

---

### Post by jfanaian on 2007-02-13
Alright I got it working. All I did was remove ndiswrapper and install the latest copy from source.

---

