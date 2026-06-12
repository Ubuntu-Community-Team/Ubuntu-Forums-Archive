---
title: "Asus X550L Weak Wifi signal with 14.04"
date: 2014-07-19
forum: Networking &amp; Wireless
---

### Post by surya6 on 2014-07-19
[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]I'm new to Ubuntu OS. I've installed ubuntu 14.04 x64 on my ASUS X550LC laptop yesterday. The wifi signal is weak & getting disconnected sometimes.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Searched all over the web but many site/forums has discussed with Atheros network adapter but the one I have is Ralink RT3290.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]This what my iwconfig gives:[/FONT][/COLOR]
[/SIZE][SIZE=3]```
ppp0      no wireless extensions.
eth0      no wireless extensions.
lo        no wireless extensions.
usbpn0    no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any  
      Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
      Retry  long limit:7   RTS thr:off   Fragment thr:off
      Power Management:off
```[/SIZE]

---

### Post by praseodym on 2014-07-20
Please show the outputs of:
```

lsmod
ifconfig wlan0
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
dmesg | grep rt2
```

---

