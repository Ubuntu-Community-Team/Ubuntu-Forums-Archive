---
title: "WiFi adapter not found"
date: 2019-02-23
forum: Networking &amp; Wireless
---

### Post by jgpfersich3 on 2019-02-23
I bought a HP Pavilion 590-p0057c and installed Ubuntu 18.04.01 on it. When I went to turn on WiFi, settings said: "WiFi adapter not found". Is there a fix for this?

lspci | grep -i network yields:

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter

---

### Post by jgpfersich3 on 2019-02-24
well, i tried the instructions in the post[ https://ubuntuforums.org/showthread.php?t=2412824&highlight=wifi+adapte]("https://ubuntuforums.org/showthread.php?t=2412824&highlight=wifi+adapter")r, but it didn't work. Still get No WiFi Adapter found.

---

### Post by jgpfersich3 on 2019-02-24
Well, since no help is forthcoming I bought a number of usb wifi sticks from Amazon, from 600mbs to 150mbs. The first I tried,
[URL="https://smile.amazon.com/gp/product/B01CCMUN8C/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1"]
EDUP  WiFi Adapter ac600Mbps Wireless USB Adapter 5.8GHz/2.4GHz Dual Band  600Mbps USB Adapter 2dBi External Antennas Supports Windows XP,Win  Vista,Win 7,Win 8.1, Win 10,Mac OS X 10.6-10.13     [/URL]has linux drivers that you have to compile. I hardwired the computer to ethernet, installed gcc, make and cmake, because the install script called for them. Once I got the tools installed, I ran the install script, and got an error 2 out of the script. The docs didn't mention an error 2, so I moved onto the next wifi adapter.

Next I tried the [URL="https://smile.amazon.com/gp/product/B00EQT0YK2/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1"]Panda  300Mbps Wireless N USB Adapter - Windows Vista/7/8/8.1/10, Mint,  Ubuntu, Fedora, openSUSE, CentOS, Lubuntu, Zorin, Kali Linux and  Raspbian Wheezy. 
[/URL]The docs said it was PnP for Linux, but it didn't mention 18.04 in the list of versions supported. It works. I turned Secure Boot back on, and it still works. So my quest for a working real OS is complete. I'd rather have a speedier connection, but it's just not worth the hassle.

---

### Post by jeremy31 on 2019-02-24
I have no idea why the instructions for the internal card didn't work, unless you happened to delete the Secure Boot keys

Plug the EDUP in and post results for ```
lsusb
```
There is a chance it might be supported by a github project

---

### Post by wildmanne39 on 2019-02-24
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by jgpfersich3 on 2019-02-24
output of lsusb with EDUP wifi dongle and Panda wifi dongle installed:

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0811 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 0bda:b00a Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2019-02-25
```
sudo apt install git dkms
git clone https://github.com/gnab/rtl8812au.git
sudo cp -r rtl8812au  /usr/src/rtl8812au-4.2.2
sudo dkms add -m rtl8812au -v 4.2.2
sudo dkms build -m rtl8812au -v 4.2.2
sudo dkms install -m rtl8812au -v 4.2.2
```
Reboot and the EDUP should work

---

### Post by jgpfersich3 on 2019-02-28
I did that and I don't know how to tell if it worked. Is there a way to switch between wifi adapters? It seems that things were easier to do in 16.04, and I know almost nothing about the wifi facilities in Linux. Or any wifi, really. i tried googling and got nowhere. Ethernet is my game at work.

---

### Post by jgpfersich3 on 2019-02-28
Well, I dug around  a little more and found iwlist, which pointed me to iwconfig. I found that I now got 2 IP addresses. After all the reboots, the internal wifi adapter has started to work, so the original fix seems to have worked. It seems that you have to reboot at least twice to get this stuff to work.

And yes, the instructions for the EDUP dongle worked perfectly.

How do I mark this as solved? Thanks for your help. A computer is only worthwhile to me if I can program in Unix on it.

---

### Post by jeremy31 on 2019-02-28
To mark as solved, find the Thread tools menu near the top right of page

---

### Post by koset2 on 2019-07-06
Jeremy, this helped me big time. Thanks!

---

