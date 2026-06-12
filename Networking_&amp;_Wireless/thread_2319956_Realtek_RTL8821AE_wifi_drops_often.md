---
title: "Realtek RTL8821AE wifi drops often"
date: 2016-04-08
forum: Networking &amp; Wireless
---

### Post by aem0512 on 2016-04-08
I'm having the worst time with my new-ish ASUS F555U and the Realtek components. I have Realtek speakers too and the sound is always garbled and weird on flash playback. 

Anyway, my main annoyance is that the wifi card stops working fairly often and I have to "sudo killall NetworkManager" and "sudo NetworkManager" to get it working again. 

Can anyone help me get the proper firmware for my Realtek components?

Here's some info from the wireless-info.txt :

##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
        Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
        Kernel driver in use: r8169


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
        Subsystem: XAVi Technologies Corp. Device [1b9a:2482]
        Kernel driver in use: rtl8821ae


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID b49a:04f2
Bus 001 Device 004: ID 0bda:57de Realtek Semiconductor Corp.
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by ghigiuolo on 2016-04-24
I have the same problem. Upgrading to 16.04 does not seem to change anything.

Any news?

---

### Post by santhony on 2016-05-20
> **ghigiuolo said:**
> I have the same problem. Upgrading to 16.04 does not seem to change anything.

Any news?


Any updates on this?

---

### Post by paul-sinnett on 2017-03-17
[COLOR=#111111][FONT=Ubuntu]I had a similar problem with a Lenovo ideapad 300 which uses the same Realtek RTL8821AE WiFi. Upgrading to 16.10 did not fix the problem. I spent almost a week trying to correct this problem, but in the end installing wicd and disabling NetworkManager fixed the problem.


[/FONT][/COLOR]

---

### Post by fayeem on 2017-03-20
Try this command to terminal i will sure its works 100%

1. sudo add-apt-repository ppa:hanipouspilot/rtlwifi

2. sudo apt-get update

3. sudo apt-get install rtlwifi-new-dkms linux-firmware

---

### Post by zbyszko43 on 2017-03-21
I am sorry for my English (second language) I did replaced network manager with Wicd 1.7.4 and connection with wireless working much better, no dropping connection any more. Kubuntu 16.10. Just like paul-sinnett did.
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)
For couple days I been keep both managers but when all been work correctly I did removed plasma network manager. Don't worry if all connection disappear from plasma manger just connect by wicd manager.

---

