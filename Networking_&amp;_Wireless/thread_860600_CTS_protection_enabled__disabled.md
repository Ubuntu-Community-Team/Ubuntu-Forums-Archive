---
title: "CTS protection enabled / disabled"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by hermes0710 on 2008-07-15
Hi all,
  I have no functionality issues at all with my wireless card but I noticed that I get a very strange log (dmesg) from this device.

```
[  193.237453] wlan0: CTS protection enabled (BSSID=xx:xx:xx:xx:xx:xx)
[  194.669106] wlan0: CTS protection disabled (BSSID=xx:xx:xx:xx:xx:xx)
[  194.873635] wlan0: CTS protection enabled (BSSID=xx:xx:xx:xx:xx:xx)
[  201.009419] wlan0: CTS protection disabled (BSSID=xx:xx:xx:xx:xx:xx)
[  201.315851] wlan0: CTS protection enabled (BSSID=xx:xx:xx:xx:xx:xx)
[  202.338428] wlan0: CTS protection disabled (BSSID=xx:xx:xx:xx:xx:xx)
[  202.440658] wlan0: CTS protection enabled (BSSID=xx:xx:xx:xx:xx:xx)
[  206.530976] printk: 4 messages suppressed.
[  206.530986] wlan0: CTS protection disabled (BSSID=xx:xx:xx:xx:xx:xx)
[  211.541593] printk: 6 messages suppressed.
[  211.541603] wlan0: CTS protection enabled (BSSID=xx:xx:xx:xx:xx:xx)
[  218.801864] printk: 4 messages suppressed.
[  218.801874] wlan0: CTS protection disabled (BSSID=xx:xx:xx:xx:xx:xx)
[  221.767332] printk: 3 messages suppressed.
[  221.767342] wlan0: CTS protection disabled (BSSID=xx:xx:xx:xx:xx:xx)
[  228.209531] printk: 5 messages suppressed.
[  228.209536] wlan0: CTS protection disabled (BSSID=xx:xx:xx:xx:xx:xx)
[  231.379523] printk: 4 messages suppressed.
[  231.379533] wlan0: CTS protection enabled (BSSID=xx:xx:xx:xx:xx:xx)
[  236.696910] printk: 3 messages suppressed.
[  236.696920] wlan0: CTS protection enabled (BSSID=xx:xx:xx:xx:xx:xx)
```

Has anybody noticed this?

My card:

Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by Sevk on 2008-07-31
[  864.609030] wlan0: CTS protection enabled (BSSID=00:11:50:b6:d5:d7)
[  867.274650] wlan0: CTS protection disabled (BSSID=00:11:50:b6:d5:d7)
[  872.742739] wlan0: CTS protection enabled (BSSID=00:11:50:b6:d5:d7)
[  875.749706] wlan0: CTS protection disabled (BSSID=00:11:50:b6:d5:d7)
[  885.073207] wlan0: CTS protection enabled (BSSID=00:11:50:b6:d5:d7)
[  887.707606] wlan0: CTS protection disabled (BSSID=00:11:50:b6:d5:d7)
[  900.685441] wlan0: CTS protection enabled (BSSID=00:11:50:b6:d5:d7)
[  903.788711] wlan0: CTS protection disabled (BSSID=00:11:50:b6:d5:d7)
[  928.044947] wlan0: CTS protection enabled (BSSID=00:11:50:b6:d5:d7)
[  928.892039] wlan0: CTS protection disabled (BSSID=00:11:50:b6:d5:d7)
[  934.590434] wlan0: CTS protection enabled (BSSID=00:11:50:b6:d5:d7)
[  935.791473] wlan0: CTS protection disabled (BSSID=00:11:50:b6:d5:d7)


mine

---

### Post by Gun_Smoke on 2008-08-08
I'm getting the same.

---

### Post by moparisthebest on 2008-08-22
I have the exact same problem, using the b43 driver.  Anyone know what it is or how to stop it?

---

### Post by kyron on 2008-09-20
I am experiencing the same problem with my mother's laptop and I have noticed that the system crawls to a halt. Even though the module isn't taking 100% CPU, the time consumed by the module is extremely high (higher than X) and the system becomes practically unresponsive until all network traffic stops and/or I unload the b43 module.

This is running the stock kubuntu 2.6.24-19 kernel + modules.

---

### Post by 01mf02 on 2008-10-14
I have the same problem as Kyron: massive CPU usage when network traffic is involved, although it seems I use the module rt73usb. (It's a Linksys Wireless-G USB adapter, if that helps anything :)).

Although I'm happy to give kudos to the Ubuntu, Kernel and NetworkManager team for making the wireless setup such a breeze, I have to say that this problem is quite a killer for me, because I can't even listen to music while I download something or load an internet page (music stutters :().

I would be glad to give more information to solve the problem.

---

### Post by vange on 2008-12-30
Slightly off topic: I noticed that with kernels higher than 2.6.24-18, CTS is enabled by default on EAP-TLS-connections even though CTS isn't enabled on the Access Point. Because of that, I can only connect to EAP-TLS-Access Points on kernel 2.6.24-18 - weird.

Have you noticed any pattern in the CTS problem and kernel version?

---

### Post by plamen_todoroff on 2009-01-07
The same messages started showing in my syslog yesterday, this is the first time such messages appear so frequently, 2 to 10 seconds between them. I guess there is a connection between the appearence of these messages and yesterdays update to the network-manager. Anyone else started getting these messages?

---

### Post by hermes0710 on 2009-01-08
> **plamen_todoroff said:**
> The same messages started showing in my syslog yesterday, this is the first time such messages appear so frequently, 2 to 10 seconds between them. I guess there is a connection between the appearence of these messages and yesterdays update to the network-manager. Anyone else started getting these messages?

I had this issue resolved by updates automatically. I will check if the new updates cause this again and i will get back to you.

---

### Post by vange on 2009-01-09
> **hermes0710 said:**
> I had this issue resolved by updates automatically. I will check if the new updates cause this again and i will get back to you.

I am having other troubles with the newest kernel update 2.6.24-21: Xorg wont start - so I am not able to try with that kernel version right now.

I just discovered I received a 2.6.24-23 kernel update, which I will boot into later today.

---

