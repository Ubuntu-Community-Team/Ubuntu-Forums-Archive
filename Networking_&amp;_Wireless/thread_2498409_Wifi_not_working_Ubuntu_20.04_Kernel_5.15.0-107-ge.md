---
title: "Wifi not working Ubuntu 20.04 Kernel 5.15.0-107-generic -"
date: 2024-06-12
forum: Networking &amp; Wireless
---

### Post by felixmertin on 2024-06-12
Hi,

I'm using a ASUS vivobook with Ubuntu 20.04 and Kernel 5.15.0-107-generic and my wireless adapter seems not to be working. I want to connect to my home router which is reachable under `All hail the Internet 2.4 Ghz` - but that does not work. Sometime the network is seen but then connecting fails. Often the network isn't even found. My iPhone and Windows Asus laptop can use it without issues.

The notebook: ASUS Vivobook Pro 14X OLED N7400PC-KM135X Notebook - Intel® Core&#8482; i7-11370H - 16GB - 512GB SSD - NVIDIA® GeForce® RTX 3050

I have updated via `sudo apt update && sudo apt upgrade` to the newest kernel. Tried several switching it off and on options via nmcli and GUI - nothing works. Also configuring the router to separate 2.4Ghz and 5Ghz network didn't help. 

The Ubuntu GUI prompts me regularly with **Activation of network connection failed**

My ethernet connection works strangely without issues.

Please help as I didn't had this issue for over a year and now it came back all of a sudden and does not go away ...

[ATTACH]293858[/ATTACH]

---

### Post by jeremy31 on 2024-06-12
About all you can do in terminal is
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo iwconfig wlo1 power off
```
Reboot and see if it works better with power management disabled

---

### Post by felixmertin on 2024-06-13
I should have noted as well - I have already tried without success:

- Disabling the power management via `iwconfig` and `default-wifi-powersave-on.conf`
- reinstalling and restarting of network manager via `sudo apt-get install -d --reinstall network-manager network-manager-gnome && sudo systemctl restart NetworkManager`
- removing all saved connections for wireless via `nm-connection-editor`

But still thanks for your swift reply.

---

### Post by currentshaft on 2024-06-13
Are you also using Bluetooth on that device?

>  The Ubuntu GUI prompts me regularly with Activation of network connection failed

Possibly the captive portal check? You can try disabling it in settings.

By the way, you may want to omit the SSID list in your troubleshooting file, it gives away your exact physical location.

---

### Post by felixmertin on 2024-06-14
currentshaft I don't know the captive portal check. Unfortunately, I cannot follow which option you are referring to in the settings.

---

### Post by felixmertin on 2024-06-14
Yesterday, the wifi connection started to work again in the middle of my work day. Via a diff - I noticed that the Power Management property via `iwconfig` switched to `off` - the actual `default-wifi-powersave-on.conf` wasn't changed.

---

### Post by felixmertin on 2024-06-14
[ATTACH]293869[/ATTACH]

---

