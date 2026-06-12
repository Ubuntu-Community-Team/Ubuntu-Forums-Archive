---
title: "NetworkManager Wireless Detection"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by mosestruong on 2006-08-03
I'm currently using NetworkManager applet 0.6.2 to manage my wireless connection and very please that WPA is easier to set on linux than Windows!

However, if I plug in my wireless card after I've logged in, or if I waked the computer up from hibernation, it no longer detects that I have a wireless device and hence does not offer me the choice to connect to wireless network. I know the card works because I can manually start wpa_supplicant to access my network. 

Are there any way that I can do apart from rebooting the computer to have NetworkManager recognise the card?

---

### Post by it.henrik on 2006-08-03
> **mosestruong said:**
> 
Are there any way that I can do apart from rebooting the computer to have NetworkManager recognise the card?


Try to restart network-manager

---

### Post by mosestruong on 2006-08-09
i dont seem to have network-manager 
is it NetworkManager?

If so, how do I restart it? do I just

```
sudo killall NetworkManager
sudo NetworkManager
```

Or do I restart Networking by
```
sudo /etc/init.d/networking restart
```

---

### Post by spdlimit120 on 2006-08-09
I am also using NetworkManager Applet 0.6.2 - Dapper Drake 2.6.15-26-386.
I have a wireless card, D-Link DWL-G650.  Previously, when I would right-click on NetworkManager it would give me the option to Enable Wireless Network, that option is no longer there.  If I left click the only option is "Wired Network" with a radio button.  My wireless card is in and receiving a signal.  If go to configure the wireless card, then I can enter the SSID (and passkey if necessary) and it will connect.  What should I do to in NetworkManager so that it will allow me to enable Wireless from the icon and it will automatically detect and connect w/o having to configure the card enter/select the SSID?
I attempted:
sudo killall NetworkManager
sudo NetworkManager

---

### Post by cevans on 2006-08-09
Use "/etc/init.d/dbus restart". This will restart NetworkManager as well, and works for me whenever NM detects my wireless card as a wired card after coming out of suspend.

---

