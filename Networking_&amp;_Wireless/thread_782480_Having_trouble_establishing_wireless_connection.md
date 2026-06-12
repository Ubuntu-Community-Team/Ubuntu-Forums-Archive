---
title: "Having trouble establishing wireless connection"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by PaoloRicardo on 2008-05-05
I'm new to Ubuntu, having just installed 8.04.

I cannot get an Internet connection. Am running on a laptop, picking up a wireless network via a Belkin 54g USB wireless adapter (F5D705AU.

Not really sure what to do to get it working but I tried the Network Manager and staretd filling in details. Got the Essid OK but when I tried to put in my network access code there is not enough space. I have WEP 128-bit security on my modem/access - i tried to enter the hex security access code (which is 26 characters long)but there is not enough space.

Can anyone give me a beginner's guide on how to get my connection working?

Thanks

---

### Post by daengbo on 2008-05-05
I'm on vacation, in an internet cafe, and away from any Ubuntu boxes, so I can't be too specific, but if the form for Network Manager is too short, try manually configuring your network using System > Administration > Network.

---

### Post by elamericano on 2008-05-05
This doesn't sound like NetworkManager. If you click the applet and select "Connect to Other Wireless Network...", you can enter "Network Name" and choose "Wireless Security", which should be "WEP 64/128-bit Hex". You can definitely enter 26 hex characters there.

If this doesn't work, maybe you can include the version of you network app and tell us what items you are selecting and the names of the fields you are filling.

---

### Post by subzero316 on 2008-05-05
Try this........Uninstall Network Manager  and install WICD .

---

### Post by PaoloRicardo on 2008-05-05
elAmericano: I'm going into System -> Administration -> Network, and choosing Wireless connection. I can enter Network name, Password Type (WEP key (hex)) but the Network password field will not take 26 characters. (I've no idea what the other tabs require (general, DNS, Hosts).

I've clicked on the Terminals icon in the top right hand of the desktop menu bar. Wired connection is greyed out, and manual cofiguration takes me back to the Network dialogue (as described.)

Don't know if it helps but from Windows XP Device Manager, I have Intel PRO/Wireless 3945 ABG Network Connection and Intel PRO/1000 PL Network Connection.

When you say 'If you click the applet and select "Connect to Other Wireless Network...", you can enter "Network Name" and choose "Wireless Security", which should be "WEP 64/128-bit Hex"' where do I find that applet and those options?

Sorry if this is basic but I'm new to Ubuntu/Linux.

Thanks

---

### Post by elamericano on 2008-05-06
> **PaoloRicardo said:**
> When you say 'If you click the applet and select "Connect to Other Wireless Network...", you can enter "Network Name" and choose "Wireless Security", which should be "WEP 64/128-bit Hex"' where do I find that applet and those options?

NetworkManager is installed by default. The applet for it is on the top panel, near the clock. When you left click on it (It looks look a computer monitor when not connected, or an ethernet cable when your plugged in, or something intuitive) you will get a list of wireless networks in range. Select your access point, enter your key, and your done. It should turn out to be as easy as you thought it should be.

You can get the names for things in the panels by right clicking and selecting "about". I hope it's there and your wireless card is already working. Let us know.

BTW, NetworkManager is the preferred way to get connected, but what you were doing should have worked too. I think that where you were entering Network Password does take 26 characters, but since it's masked, it looks like it's not moving once it's full. Just keep typing.

---

### Post by PaoloRicardo on 2008-05-06
elAmericano: OK, that did the trick. Thanks for your assistance.

Does the applet remember the passkey or will I have to input every time?

---

### Post by elamericano on 2008-05-06
It will remember and auto-join when you boot up or lose your connection - hopefully that's what you want. When ethernet is detected it will turn off your wireless and set up your wired connection with DHCP. The most you'll have to do is select the network you want from the drop-down list, if you've been out of range for several minutes. It has a great VPN plugin too, if you need that.

Buena suerte.

---

### Post by PaoloRicardo on 2008-05-06
elAmericano: thanks again. I noticed from starting and restarting that it 'remembers' so that's great. 

Not sure what VPN does and whether I need it.

---

### Post by elamericano on 2008-05-07
> **PaoloRicardo said:**
> Not sure what VPN does and whether I need it.
If you haven't heard of VPN, then you don't need it. A lot of companies and schools use that for remote access to their internal network via a username/password authentication.

You are welcome, and I hope you enjoy your Ubuntu experience. I've been using it since before NetworkManager, and the biggest issue for me was getting connected. Things are so much better now.

---

