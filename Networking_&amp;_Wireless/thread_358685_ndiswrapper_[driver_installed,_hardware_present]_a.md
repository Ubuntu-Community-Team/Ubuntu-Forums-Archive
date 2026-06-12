---
title: "ndiswrapper: [driver installed, hardware present] and then?"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by Shiroku on 2007-02-11
I have a usb wireless adapter (Sitecom WL-113 v1 **002**) that doesn' work on Kubuntu Edgy Eft.

I installed ndiwsrapper and the usb wireless adapter's driver (rt73).

if I run:
```

ndiswrapper -l

```

this is the output:
```

Installed drivers:
rt73            driver installed, hardware present

```

so, the usb wireless adapter is recognized (in fact, if I remove it, and run again 'ndiswrapper -l', the output is only "driver installed")

Now, do I need a specific command to connect to my wireless network (router in dhcp mode) ?

If I run:
```
iwconfig
```

the output is:
```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz
          RTS thr:off   Fragment thr=2346 B

wlan0     IEEE 802.11g  ESSID:"FRC"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          RTS thr:off   Fragment thr=2346 B

```

"Access Point: Not-Associated" ? What does it means?
when I connect the usb wireless adapter, there is also a wmaster0 interface.... What is it?

---

