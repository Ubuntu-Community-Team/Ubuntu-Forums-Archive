---
title: "Installing &quot;Driverless&quot; WiFi Adapter"
date: 2019-10-04
forum: Networking &amp; Wireless
---

### Post by marcowen20 on 2019-10-04
I bought a "driverless" WiFi adapter because my optical drive reader is not working. 

In Windows, when first plugged in, it acts as a 17MB usb flash drive that contains autoinstall executables for Windows and Mac. When executed, it no longer functions as a flash drive and only as WiFi adapter. It works perfectly.

I also want to install it in my second laptop which runs Ubuntu. However, even after following instructions from multiple sources online, I failed to make it work. I think the problem here is that the instructions assume that the adapter is ONLY an adapter. Any help?

The adapter has Realtek rtl8811cu.

---

### Post by slickymaster on 2019-10-04
Thread moved to **Networking & Wireless** for a better fit

---

### Post by chili555 on 2019-10-04
What instructions have you followed? Did you install the package usb_modeswitch? Did you install the appropriate Ubuntu driver for your device? Which one; a link would be very helpful. Please insert the device and run and post:

```
lsusb
```

---

### Post by marcowen20 on 2019-10-05
[https://github.com/brektrou/rtl8821CU](https://github.com/brektrou/rtl8821CU) this driver, with instructions in README.md. Everything went fine, but the adapter is still just a storage drive.

Here's the lsusb output:
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 13d3:5a11 IMC Networks 
Bus 001 Device 005: ID 0bda:1a2b Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 13d3:3506 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by chili555 on 2019-10-05
Did you install the package usb-modeswitch?```
sudo dpkg -s usb-modeswitch | grep Status
```Did you follow the other instruction from the github?```
sudo usb_modeswitch -KW -v 0bda -p 1a2b
```

---

