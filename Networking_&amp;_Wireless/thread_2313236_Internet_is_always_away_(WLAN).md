---
title: "Internet is always away (WLAN)"
date: 2016-02-10
forum: Networking &amp; Wireless
---

### Post by Michael_Berl on 2016-02-10
[COLOR=#212121][FONT=arial]Internet always away at full BandbreitenausnutzugHelloI have Ubuntu Gnome 15:10 64bit running on my Asus UX31 E and the Internet is getting away. It is a wireless, lut lspci is a Qualcomm Atheros AR9485 Wireless Network Adapter installed.The Internet is constantly away means concretely: I download with full bandwidth z.Bsp. SABNZB then I have no Internet connection, but is NOT displayed in the bar above. I then no longer come to the web interface of the router through 192.168.2.1 briefly then helps to terminate the connection (top of the bar) and to reconnect. Eventually, the connection is so slow that the web interface is built only in slow motion in the browser. By contrast, the WiFi works just fine on my phone S6. The router is a Spoeedport Entry Telekom. (No Speed &#8203;&#8203;PortSentry 2)Cairo-Dock and Conky are also installed, but remains the error, even if I finish both by the Killall command.Surface is Ubuntu Gnome Classic with Compiz[/FONT][/COLOR]

---

### Post by jeremy31 on 2016-02-10
It sounds like your wireless router may have TKIP or WEP enabled.  My AR9485 doesn't work well when I have either of them enabled for encryption, it likes WPA2 only

---

### Post by Michael_Berl on 2016-02-10
no i have only WPA2 enabled.. with AES

---

### Post by jeremy31 on 2016-02-11
Run the wireless script from [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and post the report, then we will see what it reveals

---

