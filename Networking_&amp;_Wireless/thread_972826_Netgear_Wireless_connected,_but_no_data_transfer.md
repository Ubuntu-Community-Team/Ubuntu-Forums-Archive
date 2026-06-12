---
title: "Netgear Wireless connected, but no data transfer"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by abhver on 2008-11-06
I was using 8.04 and my Netgear wireless router was rocking with it. 

I upgraded to 8.10 through network. Very well. 

Now first of all network manager is not remembring my WEP key and ask me to enter the key every time i reconnect/turn on the system. After connection is setup...no data is sent or receeived. I checked my internet through LAN port and it is  working fine. I am unable to understand, if my Netgear Wireless router has gone/died or there is some issue with new network manager/Ubuntu 8.10.

Any help/comments will work as cool air.

---

### Post by kagashe on 2008-11-06
> **abhver said:**
> I was using 8.04 and my Netgear wireless router was rocking with it. 

I upgraded to 8.10 through network. Very well. 

Now first of all network manager is not remembring my WEP key and ask me to enter the key every time i reconnect/turn on the system. After connection is setup...no data is sent or receeived. I checked my internet through LAN port and it is  working fine. I am unable to understand, if my Netgear Wireless router has gone/died or there is some issue with new network manager/Ubuntu 8.10.

Any help/comments will work as cool air.
> Right click on Network Manager applet
Click on Edit connections
Click on Wireless Tab
If you see the Wireless connection click on Edit otherwise
Click on Add
On Wireless Tab
Enter SSID (Default if you don't know)
Click on Wireless Security tab
Under Security Select WEP 40/128-bit key or 128-bit passphrase
Click on OK.

kagashe

---

### Post by abhver on 2008-11-06
thanks, kagashe

I wanted to switch to WPA, as it is more secure. Can you please let me know the same setting for that also. :KS

Thanks again in advance,
Abhishek

---

### Post by kagashe on 2008-11-06
> **abhver said:**
> thanks, kagashe

I wanted to switch to WPA, as it is more secure. Can you please let me know the same setting for that also. :KS

Thanks again in advance,
AbhishekWPA is also available where you have selected WEP but you have to set WPA in the router also and you need to refer to the router documentation to do it.

kagashe

---

### Post by superprash2003 on 2008-11-06
in your router.. you need to go to the WIRELESS Page.. and select WPA instead of WEP..

---

