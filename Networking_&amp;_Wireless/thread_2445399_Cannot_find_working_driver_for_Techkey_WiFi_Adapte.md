---
title: "Cannot find working driver for Techkey WiFi Adapter(600mbps)"
date: 2020-06-13
forum: Networking &amp; Wireless
---

### Post by cinnamon1412 on 2020-06-13
I've had a Techkey WiFi Adapter for a while and have used it on Windows 10 and 7, and it has worked so far.
I recently installed Ubuntu Desktop 18.04 LTS, my knowledge of Linux is rudimentary and I only know the basics such as installing packages, finding my kernel version, and moving and copying files from the terminal. My WiFi Adapter is only recognized as "Realtek Driver Storage" in Ubuntu and my attempts at finding a working driver have been unsuccessful.
[B]
Potentially Useful Information:

[/B]uname -r Output:
```

5.3.0-59-generic

```
When running **lsusb**, the device shows as:
```
Bus 002 Device 013: ID 0bda:1a2b Realtek Semiconductor Corp.
```
The Amazon Page:
[https://www.amazon.com/Adapter-600mbps%EF%BC%8CTechkey-Wireless-802-11ac-10-6-10-14/dp/B07LFC7VDC/ref=sr_1_7?dchild=1&keywords=techkey+wireless+usb+wifi+adapter&qid=1592065677&s=electronics&sr=1-7](https://www.amazon.com/Adapter-600mbps%EF%BC%8CTechkey-Wireless-802-11ac-10-6-10-14/dp/B07LFC7VDC/ref=sr_1_7?dchild=1&keywords=techkey+wireless+usb+wifi+adapter&qid=1592065677&s=electronics&sr=1-7)
The information sticker on the device says:
*dual band wireless adapter*
*Model: 5B12*

---

### Post by CelticWarrior on 2020-06-13
Welcome.

Try this:
```
sudo apt install build-essential -y
mkdir -p ~/build
cd ~/build
sudo apt install git
git clone https://github.com/brektrou/rtl8821CU.git
cd rtl8821CU
make
sudo make install
```

---

### Post by Eduardoecp on 2020-06-13
I have a script that did the trick here. I tested on Peppermint 10 which is based in ubuntu 18.04. 
You can open it and check for yourself. It's basically the same script Celtic Warrior posted above, with a previous installation of Git and Make (Ubuntu probably already has them installed anyway). 
Here is the link : [https://scriptips.org/2020/06/02/usb-wireless-realtek-8811cu-linux-driver/](https://scriptips.org/2020/06/02/usb-wireless-realtek-8811cu-linux-driver/)

---

### Post by cinnamon1412 on 2020-06-13
That didn't work, though when running "make" it did say
note: this is the location of the previous definition.
Due to trying another similar driver that did not work.
Edit: Oops, this was meant in reply to CelticWarrior

---

### Post by howefield on 2020-06-13
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by jeremy31 on 2020-06-13
You need to do ```
sudo usb_modeswitch -KW -v 0bda -p 1a2b
```
To switch it from USB storage

---

### Post by cinnamon1412 on 2020-06-13
> **Eduardoecp said:**
> I have a script that did the trick here. I tested on Peppermint 10 which is based in ubuntu 18.04. 
You can open it and check for yourself. It's basically the same script Celtic Warrior posted above, with a previous installation of Git and Make (Ubuntu probably already has them installed anyway). 
Here is the link : [https://scriptips.org/2020/06/02/usb-wireless-realtek-8811cu-linux-driver/](https://scriptips.org/2020/06/02/usb-wireless-realtek-8811cu-linux-driver/)

The script didn't seem to work either, it is still showing as a USB storage device sadly.

---

### Post by cinnamon1412 on 2020-06-13
> **jeremy31 said:**
> You need to do ```
sudo usb_modeswitch -KW -v 0bda -p 1a2b
```
To switch it from USB storage
Doing that combined with the script Eduardoecp provided worked, currently replying to this on working Wi-Fi.
Thank you all for the help!

---

### Post by jeremy31 on 2020-06-13
To automate that see [https://askubuntu.com/questions/1080944/automatically-use-usb-modeswitch-for-wifi-usb/1082418#1082418](https://askubuntu.com/questions/1080944/automatically-use-usb-modeswitch-for-wifi-usb/1082418#1082418)

---

