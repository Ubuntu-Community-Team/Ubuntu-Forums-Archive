---
title: "D-Link wireless router"
date: 2023-07-31
forum: Networking &amp; Wireless
---

### Post by rm70 on 2023-07-31
I install Ubuntu 10.6 on my little netbook and need to set a up wireless connection in the editing wireless connection1 window it ask for BSSID . I don't see that on my wireless router. the router has password, WiFi name[SSID]  and WAN MAC. The Ubuntu editing widow asks for  SSID:, Mode: BSSID,,MAC Address and MTU. Can some please help me figure out what my BSSID is, Thanks 
:

---

### Post by chili555 on 2023-07-31
> I install Ubuntu 10.6 on my little netbook10.06? Did you really install a 13-year-old version of Ubuntu? We've made quite a few improvements since 2010.

In a terminal, run:
```
lsb_release -a
```
and post the result.

---

### Post by rm70 on 2023-07-31
no lbs modules found

---

### Post by chili555 on 2023-07-31
> **rm70 said:**
> no lbs modules foundlsb, not lbs.

Try this:

```
uname -r
```

---

### Post by him610 on 2023-07-31
If the OP really has a netbook from 10 to 15 years ago, it is a 32 bit machine. I believe LTS 18.04 was the last 32 bit release of ubuntu. I have one of those 32 bit netbooks that I installed Debian 11 on just last year. It runs as expected - a little slow, but it does run.

---

### Post by rm70 on 2023-08-01
out put for uname -a is: 2.6.32.38 generic

---

### Post by rm70 on 2023-08-01
I tried Debian 12 bookworm but found out there is bug for B43/ucode15.fw that after trying couldn't get resolved plus it ran super slow so I reinstalled 10.04. It runs run very well just need to get my WiFi figured out. I'm no Linux guru although I do like learning.

---

### Post by rm70 on 2023-08-01
Thanks Chili555 I did enter lsb, lbs was just a typo on my part.

---

### Post by chili555 on 2023-08-01
> **rm70 said:**
> out put for uname -a is: 2.6.32.38 generic
A 2.6 kernel version! This is your lucky day. There are only a few networking specialists on this forum that even remember kernel version 2.6 but I'm one of them!

Are you quite sure you have a wireless interface? Are these commands productive?

```
iwconfig
sudo iwlist scan
```

There is no need to see the results, just confirm that they produce credible results.

If so, then I strongly suspect that you will not need to specify the BSSID. 

In addition to the driver and firmware, did you install wpa_supplicant? 

```
sudo dpkg -s wpasupplicant | grep Status
```

If your router is encrypted with WPA, as it should be, you will need wpa_supplicant. I am not certain, however, that the versions of the driver and wpa_supplicant supplied for kernel version 2.6 will do WPA2. Your router may do WPA/WPA2 and autoselect depending on the client, that is, your netbook.

---

