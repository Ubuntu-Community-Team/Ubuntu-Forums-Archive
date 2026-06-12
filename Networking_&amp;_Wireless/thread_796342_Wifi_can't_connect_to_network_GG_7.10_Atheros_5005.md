---
title: "Wifi can't connect to network GG 7.10 Atheros 5005GS"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by hakujin1 on 2008-05-16
I am running an Atheros mini-pci card on a Dell Latitude C610.

Win XP Pro calls this wireless card an Atheros AR5005GS, however, Ubuntu thinks its an AR5212.

At any rate, I have installed Gutsy Gibbon release (7.10) and am a total n00b. I presume that the 7.10 disc installed the appropriate madwifi drivers as I can see my wireless routers using sudo iwlist ath0 scan or through Network Settings --> Properties --> network name drop down. So through the GUI (Network Settings) I added my preferred ssid, password type, my WPA key and DHCP. It looks like it takes as the 'changing interface config' bar pops up but still no connection and when I open up the wireless connection properties again, the WPA field is blank. In addition, on the Network Settings dialog box, location is blank and when i click the drop down, the input field box changes color shade and a horizontal line strikes through the box. Lastly, I can see the Atheros HAL in the restricted drivers dialog; it's check and in use.


What must I do to get WiFi rolling in Ubuntu on my Dell C610 laptop? Your help is greatly appreciated.

TIA

---

### Post by hakujin1 on 2008-05-16
following the howto wifi sticky remedied my situation as I can now connect but not w/o restarting networking each time I restart. I tried the howto's creation of a script but to no avail. I have to manually do it via bash after each start. Still though... glad to finally have wifi connect.

---

### Post by Snappo on 2008-05-16
> **hakujin1 said:**
> following the howto wifi sticky remedied my situation as I can now connect but not w/o restarting networking each time I restart. I tried the howto's creation of a script but to no avail. I have to manually do it via bash after each start. Still though... glad to finally have wifi connect.

erm link me to the thread i have the same card and can't even get the wireless icon to show...

---

### Post by hakujin1 on 2008-05-22
> **Snappo said:**
> erm link me to the thread i have the same card and can't even get the wireless icon to show...

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

