---
title: "Wifi Keeps disconnecting and needs reauthentacation - Ubuntu 20.04"
date: 2020-12-02
forum: Networking &amp; Wireless
---

### Post by wingrider78 on 2020-12-02
I am using a "new to me" Dell Latitude E6440 laptop with a fresh install of ubuntu 20.04. Everything has worked great, except starting today, I am getting a ton of error messages that the wifi needs reauthentication. It will happen anywhere from 3-5 times per minute, up to 3 times an hour...not sure why it is happening.

Nothing has changed on the network since buying the laptop and putting it into service. 

I have tried powering down and restarting the laptop, powering down and restarting the router ([NETGEAR Nighthawk X6 Smart WiFi Router (R8000) - AC3200]("https://www.amazon.com/gp/product/B00KWHMR6G/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1")), powering down and restarting the cable modem (given to us by Spectrum) with no luck.

I have connected to my own hotspot via my smartphone (galaxy s9 on verizon) and didn't have any connection issues over the course of 8 hours using it. Started using the house wifi again, and within the first 10 minutes, I was getting the authentication errors again. No other devices are having issues. I have three TVs and a desktop (ubuntu 20.04) wired to the router, 3 chromebooks in use while I was using the laptop and a cell phone, that didn't have any disconnect issues during the entire time I was having mine with the laptop.

I have run the update commands in the sticky and still having the issues. I will attach the tar file of the output of the network script.

If you have anything that will help me, please let me know.

[ATTACH]287499[/ATTACH]

---

### Post by morrownr on 2020-12-05
Given your description, I would look at router settings first:

Recommended Router Settings for WiFi:


Note: These are general recommendations based on years of experience but may not apply to your situation so testing to see if any help fix your problem is recommended.


Security: Use WPA2-AES. Do not use WPA or WPA2 mixed mode or TKIP.


Channel Width for 2.4G: Use 20 MHz. Do not use 40 MHz or 20/40 automatic.


Channels for 2.4G: Use 1 or 6 or 11. Do not use automatic channel selection.


Mode for 2.4G: Use G/N or B/G/N. Do not use N only.


Network names: Do not set the 2.4G Network and the 5G Network to the same name. Many routers come with both networks set to the same name.


Power Saving: Set to off. This can help in some situations. If you try turning it off and you see no improvement then set it back to on so as to save electricity.


After making these changes, reboot the router.

---

### Post by praseodym on 2020-12-05
You are living in the US? If yes, set the country code:

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=US/g" /etc/default/crda
sudo systemctl stop NetworkManager.service 
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
sudo systemctl start NetworkManager.service 
```

---

