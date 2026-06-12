---
title: "USB Wireless WLAN Device"
date: 2021-08-05
forum: Networking &amp; Wireless
---

### Post by shayf on 2021-08-05
Name: Shay Fencski
Distribution: Ubuntu 20.04
Kernel: 5.8
Device: 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Driver: RTL8188eus from [lwfinger's Repository]("https://github.com/lwfinger/rtl8188eu")
Problem: Device completely disconnects from system after a good chunk of time.

I have a USB Wireless adapter that works correctly for like 20 minutes and then after 20 minutes the entire device disconnects from the system. As if I unplugged it myself..
I've turned off power saving, blacklisted the device, everything that I could possibly find online. I've been waiting 3 days for people to get back to me in a Ubuntu related discord server, yet not a single person has replied to me or even attempted to.

journalctl doesn't show anything, it just shows that it was disconnected, as if it were unplugged..

All USB ports work, power delivery is really not a problem, I don't run much off the board and its got a 700w power supply. Overkill for this machine but it's what I had on hand. I really need some help because this is my server rig and like I said it's already been down for 3 days, I'm getting quite desperate to get this working.

---

### Post by morrownr on 2021-08-05
Shay,

This reply is likely not what you were looking for but I have no experience with that usb wifi adapter. What I will offer is some information.

For situations that require dependability (24/7/365) I go with adapters that use in-kernel drivers. There are so many ways for adapters that use out-of-kernel drivers to break.

Here is a repo that I maintain that has information and links to MANY usb wifi adapters that work with in-kernel drivers:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Let me know if you have questions.

Good luck,

morrownr

---

