---
title: "Need help connecting ubuntu to network"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by needhelp101 on 2007-03-13
Hi,

I have a laptop running Ubuntu (Live CD) and need to connect it to my home etwork to download stuff and get on the interent. I have the cables but the network has xp pc's on it. Can i just plug in cable and sufr internet. if so how? what do i need to do this???

TIA

---

### Post by moshuptrail on 2007-03-13
You should be able to plug in a cable and surf from the Ubuntu laptop.

As to exchanging files with XP, that gets a bit more complex.  Windows uses specific protocols for file sharing.  Lucky for you, someone (or several) have written something called Samba that enables file sharing with windows.  So if your XP PCs have file sharing turned on and published shares, you can install Samba.  It's not always easy - there are some configuration things to do, but with some searching and reading you'll be able to get it working.

---

### Post by quakeboy on 2007-03-13
First go to System->Administration->Networking.
Enter the root password.

It shows a list connections. Select Ethernet connection. if it says its not active. then click on the active button. Double click that to open up the properties.

Enter your ip address. usually i use 192.168.1.XXX. then the subnet mask is 255.255.255.0. coz all pcs in my network use the 192.168.1.XXX series.

Make sure your ip address belongs to current network ip series.


-----Well if you need to connect to internet through LAN. I think you must have configured a Proxy Server. Just find out the proxy address and 

Edit->Preferences->general->Connection Settings
Either try auto config or enter the Manually HTTP Proxy address.

----Or if u directly connect to internet through ADSL Router + Modem. Enter the Routers ip address in the Gateway field. Then click the DNS Tab to configure your DNS servers.

Please post after trying these

---

### Post by needhelp101 on 2007-03-13
Thank you. Will try and report back.

---

### Post by needhelp101 on 2007-03-13
Works. thank you.

---

