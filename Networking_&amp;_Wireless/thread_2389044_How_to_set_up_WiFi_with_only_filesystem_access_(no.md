---
title: "How to set up WiFi with only filesystem access? (no shell, no desktop)"
date: 2018-04-10
forum: Networking &amp; Wireless
---

### Post by CoolRanchLuke on 2018-04-10
I'm trying to automate flashing an embedded linux (Tegra TX2) system, and get it up and running on wifi without having to plug in a keyboard and mouse. The regular flashing process works great, but merely adding my wifi SSID / PSK to wpa_supplicant.conf is not having the expected effect (the board does not connect to wifi on boot up). IF I plug in a screen, and mouse and keyboard, and set up the wifi manually from the Ubuntu desktop, everything works fine.

I have access to the rootfs prior to flashing the device, and can edit any files I like. I would like to be able to configure Wifi without having to run any commands on the target device, and without having to attach any keyboard / mouse / screen to the target device.

Has anyone done this before? Other than wpa_supplicant.conf, what other files are being modified when I connect to WiFi via the desktop menu / interface?

---

### Post by chili555 on 2018-04-10
If you boot to a desktop, I suspect that Network Manager is running and does all the work for you. When you boot to a command line, which is the case headless, NM can't run as it's a graphical application.

I recommend that you set up /etc/network/interfaces: [https://askubuntu.com/questions/245806/what-is-the-correct-syntax-for-etc-network-interfaces/245970#245970](https://askubuntu.com/questions/245806/what-is-the-correct-syntax-for-etc-network-interfaces/245970#245970)

Of course, substitute your wireless interface if not wlan0. I suggest a static IP so that you can ssh and ftp into it. That's difficult to do with DHCP as the address can and will change from time to time.

Post back if you get stuck or need further guidance.

---

### Post by CoolRanchLuke on 2018-04-11
Thanks, I'll give that a try.

---

