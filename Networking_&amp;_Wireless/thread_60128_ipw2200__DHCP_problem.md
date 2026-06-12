---
title: "ipw2200 / DHCP problem"
date: 2005-08-26
forum: Networking &amp; Wireless
---

### Post by gorth on 2005-08-26
Hello

I have a problem with my ipw2200 wireless card. I've compiled a vanilla 2.6.12.5 kernel in combination with ieee80211-1.0.3, ipw2200-1.0.6 and ipw2200-fw-2.3. Everything compiles and I'm able to insert the module on startup as evidenced by the following dmesg output:

Aug 26 17:13:54 localhost kernel: ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
Aug 26 17:13:54 localhost kernel: ipw2200: Copyright(c) 2003-2004 Intel Corporation
Aug 26 17:13:54 localhost kernel: ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

The problem is  acquiring an IP adress from my DHCP server on startup. It just hangs on startup and eventually times out. The weird thing is that I'm only able to  acquire an IP adress _after_ I manually do a 'iwlist eth1 scanning'. How can I overcome this problem?

Thanks

---

### Post by jpkotta on 2005-08-26
try adding

```

if [ ! -x $IWCONFIG ]; then
   exit 0 
fi

iwlist $IFACE scan


``` 

to /etc/network/if-pre-up.d/wireless-tools.

I haven't tested this, it's just a hunch.

---

