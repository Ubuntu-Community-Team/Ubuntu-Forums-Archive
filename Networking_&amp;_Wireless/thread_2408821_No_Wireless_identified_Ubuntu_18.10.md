---
title: "No Wireless identified Ubuntu 18.10"
date: 2018-12-23
forum: Networking &amp; Wireless
---

### Post by mikejamesh on 2018-12-23
Hi I am a newbie as far as Linux is concerned and I am struggling with an issue. I wonder if anyone can help? I have a new HP Pavilion Laptop that I want to convert to Ubuntu to have play? Everything seemed to be ok on the install until the system wanted to download updates during the installation. The system does not appear to recognise the wireless device. I am currently using a bit of steam technology, A Net Gear Dongle that is like a house brick!

Can anyone tell me, how I can get Ubuntu to recognise the internal wireless device.

If you can keep it simple, I am Old and Grey and quite new to Linux and Ubuntu.

Many Thanks

Mike

---

### Post by jeremy31 on 2018-12-23
Moved to Networking and Wireless
Please post results from terminal for ```
lspci -nnk | grep -iA3 net; mokutil --sb-state
```

---

### Post by chili555 on 2018-12-23
> If you can keep it simple, I am Old and Grey and quite new to Linux and Ubuntu.
I will do my very best. I doubt that you are older or greyer than me, however.

I assume it is a USB dongle. Please open a terminal with Ctrl+Alt+t and run:```
lsusb
```Post the result and we'll proceed.

---

### Post by mikejamesh on 2018-12-27
Hi Jeremy, apologies for the delay, been away doing my Winter job (Short, fat and round in a red suit may give a clue :-)

Results of your command are 

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
    Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless Network Adapter [103c:831a]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:84be]
    Kernel driver in use: r8169
    Kernel modules: r8169
SecureBoot disabled

---

### Post by mikejamesh on 2018-12-27
Hi, thanks for the reply and apologies for the delayed response. The results of the lsusb command are

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b00a Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0408:5300 Quanta Computer, Inc. 
Bus 001 Device 002: ID 0846:6a00 NetGear, Inc. WG111v2 54 Mbps Wireless [RealTek RTL8187L]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


But this just shows the temporary fix I am running at the moment which is an ancient Netgear dongle. I am trying to find out how to pick up the HP internal wireless component

Mike

---

### Post by chili555 on 2018-12-27
Please check here: [https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce](https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce)

---

### Post by mikejamesh on 2018-12-28
Hi Chili555' I followed the links and using the options available, I now have a working wireless network. 

Thank you very much. Are you much older than 1949 then :-) 

PS How do I close the question and ensure you get the praise you deserve

Mike

---

### Post by chili555 on 2018-12-28
Please use thread tools at the top to mark Solved.

I was in grade school and had my very first set of glasses when you were born.

---

### Post by mikejamesh on 2018-12-28
In which case I acknowledge my elders and betters. Thanks for all the advice, I have a working wireless system and I am one happy bunny! Thread marked as closed, Hope you have a Happy New Year
Mike

---

