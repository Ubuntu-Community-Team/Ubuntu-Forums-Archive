---
title: "Problem connecting with BCM4318 Rev2 chip"
date: 2014-06-25
forum: Networking &amp; Wireless
---

### Post by arry487 on 2014-06-25
Hello,

I am unable to see any wireless devices using this chip in my Dell inspiron 1300 laptop.

I followed the guide and flashed the new firmware for the card, the cards pci id is [14e4:4318]

Everything is configured correctly in the network connections tab but using the WIFI Radar program nothing shows up when there are several wireless devices nearby.

Thanks

Arry

---

### Post by chili555 on 2014-06-25
How about letting us see:```
rfkill list all
dmesg | grep b43
nm-tool
```Thanks.

---

### Post by arry487 on 2014-06-25
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

### Post by chili555 on 2014-06-25
> 0: phy0: Wireless LAN
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: yes[/COLOR]This strongly implies that the wireless switch or key combination (Fn+F4 or similar) is set to turn the wireless off. Can you please enable it and see if you connect?

---

### Post by arry487 on 2014-06-26
Yes the laptop has a radio button (F2)  but nothing happens when I press it, is there a way to make it work?

Thanks for your help

Tom

---

### Post by chili555 on 2014-06-26
> **arry487 said:**
> Yes the laptop has a radio button (F2)  but nothing happens when I press it, is there a way to make it work?

Thanks for your help

TomPossibly. What is the brand and model of the laptop? What does this tell us?```
lsmod
```Thanks.

---

### Post by arry487 on 2014-06-27
Ok so I managed to get it working by taking the battery out and shorting the cmos battery.

The wireless is working now and is all on all of the time.

Thnaks for your help

---

### Post by chili555 on 2014-06-27
> **arry487 said:**
> Ok so I managed to get it working by taking the battery out and shorting the cmos battery.

The wireless is working now and is all on all of the time.

Thnaks for your helpGlad it's working.

---

