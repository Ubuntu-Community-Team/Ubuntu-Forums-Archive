---
title: "How do I set up a WIFI AP"
date: 2019-09-13
forum: Networking &amp; Wireless
---

### Post by hk42 on 2019-09-13
Using a Beelink BT3 pro mini PC with 19.04.
Every thing is working fine .
But as this device is wired by gigabit Ethernet and conveniently
located I would like to use it as an access point for phones and tablets.
How do I do that ?

---

### Post by pcfan1234 on 2019-09-13
Do you have installed the NetworkManager?
Then you can click the wireless/network icon and click Edit Connections. Then go to Add (the plus).
Add a wireless network.
Type a SSID, select HotSpot as mode, this is important.
In device select your WiFi adapter.
In security you can set up authentication with a password (WPA) or you can select open (no password, everybody ca connect). The save this. Click the network icon in you taskbar again and select you created network.

---

### Post by hk42 on 2019-09-13
Thanks 
I don't seem to have an application called NetworkManager.
I found one called Network tools and yes well hidden there is an hot spot option.
Seems nice as it allows to choose the band and the channel used.
I'll give it a try and report the result.

---

### Post by hk42 on 2019-09-14
Well no luck with the access point .
May be this function of my broadcom chip is not yet supported.
BTW I found the /usr/sbin/[COLOR=#000000]NetworkManager but if I launch it nothing happens at all.[/COLOR]

---

### Post by pcfan1234 on 2019-09-14
Do you have the network icon in your top bar in GNOME?
This is the NetworkManager.

---

### Post by hk42 on 2019-09-14
Yes I have it and it is starting from here that I get an error when trying to start the hotspot.

---

### Post by hk42 on 2019-09-24
Success
As I have also XFCE I found in the "Settings" menu an entry called :
"Advanced Network Configuration"
It listed the previously added entry for the access point.
For good measure I added one as XFCEAP and it worked.

---

