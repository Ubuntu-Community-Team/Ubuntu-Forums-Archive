---
title: "Problem connecting to home wireless network"
date: 2013-09-20
forum: Networking &amp; Wireless
---

### Post by Mortificator on 2013-09-20
Hello,
I recently moved to Ubuntu 13.04 on my laptop and the university network still works just fine but I suddenly can't connect to my home WiFi (not just internet, I see my home network but can't connect to it at all)
I am fairly new to linux so i'm not sure what information to provide for this.

I am using Edimax [COLOR=#333333][FONT=Verdana] BR-6524N Wireless Router

When I run iwconfig I get:
lo         no wireless extensions.
[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]eth0    no wireless extensions.
[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]eth1   IEEE 802.11abg    ESSID: off/any
          Mode:Managed    Access Point: Not-Associated
          Retry    long limit:7   RTS thr:off   Fragment thr:off
          Power Management: on
[/FONT][/COLOR]
When I check network cards (using [COLOR=#111111][FONT=Consolas]lspci | egrep -i --color 'network|ethernet' [/FONT][/COLOR] I get:
01:00.0 Ethernet controller: Qualcomm Atheros AR8162 Fast Ethernet (rev10)
02:00.0 Network controller: Broadcom Corporation BCN4313 802.11b/g/n Wireless LAN Controller (rev01)


Thanks!

---

### Post by Kirboosy on 2013-09-20
What kind of encryption/security are you running on your home network? Are you sure that you are using the correct passphrase to connect?


~Caboose

---

### Post by Mortificator on 2013-09-20
Connection is done using WEP (64-bit, HEX) password.
I opened the security details on my PC (which runs windows 7) and copied the passphrase from there.

Come to think of it, when I try and edit the connection on my laptop the options there don't have WEP 64-bit (only WEP 40/128-bit-key, WEP 128-bit Passphrase, Dynamic WEP)

---

### Post by Kirboosy on 2013-09-20
If you are able too you might want to update your Wifi security. I would recommend at minimium WPA encryption if your wifi cards support it.)

~Caboose

---

### Post by varunendra on 2013-09-21
> **Caboose885 said:**
> If you are able too you might want to update your Wifi security. I would recommend at minimium WPA encryption if your wifi cards support it.)
.. or the best - WPA2-PSK with AES encryption, (no TKIP, and definitely not WPA/WPA2 mixed mode).

We are currently seeing some issues with this card (and a couple other broadcom ones), so can't guarantee any quick and sure-shot fix, but it may help a lot if you can provide us a detailed report of your wifi setup.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the report, please use 'Code' box to preserve the formatting. Please follow the "Using Code Tags" link in my sig. to see how.

---

