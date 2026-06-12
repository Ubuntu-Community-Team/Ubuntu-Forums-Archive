---
title: "How to install OurLink AC600 USB Wifi Adapter on Ubuntu 16.04.03 LTS?"
date: 2018-01-01
forum: Networking &amp; Wireless
---

### Post by bluevisionist on 2018-01-01
I've recently bought this wifi adapter from Amazon and it works great on Windows 10 [https://www.ourlink.us/collections/some/products/glam-hobby-600mbps-mini-802-11ac-dual-band-2-4g-5g-wireless-network-adapter-usb-wi-fi-dongle-adapter-with-2dbi-antenna-support-windows-xp-win-vista-win-7-win-8-1-win-10-mac-os-x-10-6-10-11-5](https://www.ourlink.us/collections/some/products/glam-hobby-600mbps-mini-802-11ac-dual-band-2-4g-5g-wireless-network-adapter-usb-wi-fi-dongle-adapter-with-2dbi-antenna-support-windows-xp-win-vista-win-7-win-8-1-win-10-mac-os-x-10-6-10-11-5) 

 Unfortunately, I could not get any of the drivers to work on Ubuntu and was wondering if anyone can help? I have an ethernet connection ready. I tried some rtl8812au drivers but still no luck. I am also new to Ubuntu so step-by-step instructions would be greatly appreciated. :)

---

### Post by Hadaka on 2018-01-02
Hi, please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the **wireless-info.txt**

Then do..
```
lsusb
```
*If you see...[COLOR=#000000]ID [/COLOR][COLOR=#ff0000]0bda[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#ff0000]a811[/COLOR][COLOR=#000000] Realtek Semiconductor Corp.
then..
[/COLOR][COLOR=#000000][INDENT]From a WORKING WIRED connection...Please follow the instructions in post # 5 here..
[https://ubuntuforums.org/showthread....6#post13705226]("https://ubuntuforums.org/showthread.php?t=2375603&p=13705226#post13705226")
Thanks.[/INDENT]


[/COLOR]

---

