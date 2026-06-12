---
title: "Motherboard ASUS Z170i Pro gaming, Ubuntu 15.10, integrated wifi dont work."
date: 2016-01-26
forum: Networking &amp; Wireless
---

### Post by MuR3 on 2016-01-26
Hi.

 This is my first post in this forum, I'm pretty hopeless with a problem and I would like to ask for help for it, the following occurs:

 I have an ASUS Z170i Pro Gaming newly installed Ubuntu 15.10, the installation process went well, but this board integrated wireless card does not work, the system detects the wireless chip for a few minutes and see networks, but it is impossible to connect with them.

 I have tried countless combinations, my system is fully updated and wifi does not work, it is important that the pc I have a site where I can not get with cable.

 Thank you very much for your time, a greeting.

---

### Post by Vladlenin5000 on 2016-01-26
Hi and welcome.

Before anything else we need to determine what that WiFi chipset really is... The Asus website is of no use. Try, in the terminal, both *lspci* and *lsusb *commands before anything else and post the relevant info (only the line regarding the wireless device is relevant but if you're unsure post the full results).

Reading the sticky thread [Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108") is a must as it provides additional instructions for running a troubleshooting script that we might need later but for the moment just knowing what hardware are we dealing with should suffice and that can be determined by one of the commands in the first paragraph.

---

### Post by MuR3 on 2016-01-26
> **Vladlenin5000 said:**
> Hi and welcome.

Before anything else we need to determine what that WiFi chipset really is... The Asus website is of no use. Try, in the terminal, both *lspci* and *lsusb *commands before anything else and post the relevant info (only the line regarding the wireless device is relevant but if you're unsure post the full results).

Reading the sticky thread [Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108") is a must as it provides additional instructions for running a troubleshooting script that we might need later but for the moment just knowing what hardware are we dealing with should suffice and that can be determined by one of the commands in the first paragraph.

Hi, thx for the quick response.

lspci tell me this: 05:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)


I Attach the wireless-info.tar.gz too, i hope will be usefull.

Thx a lot.

---

### Post by Vladlenin5000 on 2016-01-26
Atheros QCA6174 is really new but should be supported by the kernel series in 15.10.
The script output shows that both the correct driver and firmware are being loaded (apparently) but there's also errors I'm not familiar with. So...

For the moment and considering that > the system detects the wireless chip for a few minutes and see networks, but it is impossible to connect with them then I suggest you check the wireless settings at the router and choose the recommended encryption settings - WPA2-AES (not TKIP and not any mixed mode). If it doesn't help then please describe exactly what happens when you try to connect to your network.

---

### Post by MuR3 on 2016-01-26
Hi.

My router settings is correct for multiple computers , laptops , phones and other devices connect seamlessly with Linux .

I spent several hours testing with several drivers , firmware , etc and now I found this : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1520343/comments/19](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1520343/comments/19)

Tomorrow I 'll try , because I do not have the equipment front , and if I comment this solution corrects this failure of the wifi in this motherboard with Ubuntu 15.10 .

Greetings and thank you.

---

