---
title: "Can't bring wlan up with rtl8723ae driver"
date: 2016-11-09
forum: Networking &amp; Wireless
---

### Post by ugarth on 2016-11-09
Hello !

I have a wireless card from Realtek in my laptop. With Ubuntu version's 15.* I would already see the network going down now and then every couple hours, and to reenable it I would have to remove and insert the kernel module again, using modprobe.

Now with version 16.04 (kernel 4.4) and 16.10 (kernel 4.8) the problem became more serious. Two thirds of the times after I boot the laptop, there is no wifi, meaning, the wlan1 interface is down. The rtl8723ae module is loaded, the hardware is detected, and it works now and then, and works in windows too so it's not a hardware problem. No matter what I try, I can't bring the interface up and scan for networks.

```

$ sudo ifconfig -v wlan1 up
$ nmcli d s
DEVICE  TYPE      STATE         CONNECTION
eth1    ethernet  connected     Wired connection 1
wlan1   wifi      disconnected  --
lo      loopback  unmanaged     --
$ sudo iwlist scan
lo        Interface doesn't support scanning.
wlan1     No scan results
eth1      Interface doesn't support scanning.
```

Full output of the wireless_script, can't see anything interesting.
[ATTACH]272054[/ATTACH]

Thank you so much for your time and help :)

---

### Post by Hadaka on 2016-11-09
Hi please post the output of..
```
grep [[:alnum:]] /sys/module/rtl8723ae/parameters/*
```
thanks

---

### Post by ugarth on 2016-11-10
Howdy

```
$ grep '[[:alnum:]]' /sys/module/rtl8723ae/parameters/*
/sys/module/rtl8723ae/parameters/debug:5
/sys/module/rtl8723ae/parameters/disable_watchdog:N
/sys/module/rtl8723ae/parameters/fwlps:Y
/sys/module/rtl8723ae/parameters/ips:Y
/sys/module/rtl8723ae/parameters/msi:N
/sys/module/rtl8723ae/parameters/swenc:N
/sys/module/rtl8723ae/parameters/swlps:N
```

And now wifi is working again... grrr... seems like some race condition perhaps during boot ? I tried booting with upstart, the computer didn't go anywhere.

---

### Post by ugarth on 2016-11-10
I also tried the driver from [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) Same result, so it might be something with the firmware blob.

---

### Post by Hadaka on 2016-11-10
Hi, give this a go..
This will insure the rtl8723ae module is loaded on boot.
```
echo rtl8723ae | sudo tee -a /etc/modules
```
Let's massage some of the parameters
```
echo "options rtl8723ae swenc=1 fwlps=0 ips=0 msi=1" | sudo tee -a /etc/modprobe.d/rtl8723ae.conf
```
boot and test
thanks.

---

