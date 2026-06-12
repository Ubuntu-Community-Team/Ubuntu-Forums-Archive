---
title: "No Connect button in Wifi Radar?"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by nyxynyx on 2006-12-26
Hello. I have a fresh install of Edgy. I have wifi radar but I dont have the Connect button in it. How can I get that button back? Thanks!

---

### Post by nyxynyx on 2006-12-30
*Bump!

I see a Disconnect button instead of a Connect button. I press Disconnect but nothing happens. On my other system I see the Connect button. Any idea?

---

### Post by nyxynyx on 2006-12-31
Anybody?:KS

---

### Post by hotani on 2007-01-06
Same here. I'm a little confused about the operation of this app since there is no 'connect' button. Tried deactivating the wireless config in networking but still no 'connect'.

---

### Post by odnetin on 2007-01-15
I had the same problem with the 'connect' button missing in wifi-radar. i try install and uninstall and use my limited knowledge of command line to fix it but fail so i resort to other means to connect. i find the following useful. at least it works very well for me!

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

it said the guide is for 6.06 but i try it on 6.10 and connect to the WPA secure network right away.
hope it helps!

---

### Post by Skidpad on 2007-01-16
New Edgy user here, just installed two weeks ago on this laptop.

Mine has never had a "connect" button.  To activate a wireless connection, I use WiFi Radar to determine the SSID (network name), and then go into Network Settings (System>Administration>Networking), select your wireless connection/card, click Properties, and then type the SSID obtained using WiFi Radar in the ESSID box.  You wouldn't think you can edit the name in that box, but you can.

Once the SSID is entered, make sure "Enable this connection" is checked, and click OK.  (If you are connecting to an encrypted network, enter your passkey in the boxes as well).  Back on the main Network Settings screen, make sure your wireless connection/card is checked, and the system should then activate and connect to the SSID you just entered.  You will see a status bar as it activates the connection.

This has worked for me on two networks now.  Hope this helps.

:)

---

### Post by ileavache on 2007-01-18
I do exactly the same as Skidpad (View network list with WiFi Radar then connect using System > Administration >  Network Settings). This works just fine. However, this is a regression in 6.10 as in 6.06 the NetWork Name drop down was able to give the same detected network list as a radar. Not a big deal but annoying when you move from one site to another.
Also, I have never ever seen any connect button in the radar and radar buttons have never done anything!

---

### Post by frick on 2007-01-21
I found that when I had the proper channel selected in WIFI-Radar that it connected and the buttons started working... For my wireless router it was channel 6. (with all wep turned off.  My problem is that I have not found a way of turning WEP or WPA on in 6:10.

I am using a Orinoco Gold Pcmia card (it worked right of the box with a fresh install of 6;10. (with no WEP)

Frick

---

