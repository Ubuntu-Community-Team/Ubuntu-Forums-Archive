---
title: "Now Ubuntu won't connect to wireless"
date: 2013-11-16
forum: Networking &amp; Wireless
---

### Post by rva1945 on 2013-11-16
4 hours before I had been using it ok. Now, I turn the PC on and no matter which user I logs in, it says

Network
Disconnected: you are now offline

The wireless icon seems to be "empty", right clicking on it, the menu says Enable newtorking and it is enabled.

And of course I can connect with my tablet or another PC.

What happened?

---

### Post by grahammechanical on 2013-11-16
Does it say Enable WiFi? And is it enabled? Perhaps the wireless adapter card is turned off.

```
rfkill list
```

The report should not say that it is blocked in either software or hardware.

Regards.

---

### Post by rva1945 on 2013-11-16
It says:

0:phy0: Wireless LAN
          Soft blocked: yes
          Hard blocked: no
1: brcmwl-0: Wireless LAN
          Soft blocked: yes
          Hard blocked: no
2:Ideapad_wlan: Wireless LAN
          Soft blocked: yes
          Hard blocked: yes

?

---

### Post by rva1945 on 2013-11-16
lspci gives (among other data):

05:0.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireles Network Adapter (rev 01).

I tried many suggestions found in the forum, but none worked.

Ubuntu 12.04 is the only o.s. in this Lenovo laptop, no dual boot.

It has been working ok for months since I installed 12.04. But today, after having used it ok in the morning, now it refuses to enable wireless newtorking.

sudo service wireless start
gives
wireless: unrecognized service.

---

### Post by rva1945 on 2013-11-16
I installed W7 in available disk space, and the problem remains. WLAN AutoConfig service was not started, but then I started it and even set its startup to Automatic, and it starts after reboot, but no wireless.

In BIOS, Wireless LAN support is enabled.

Do I have to consider the hardware is failing?

---

