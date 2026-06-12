---
title: "Network Manager, WEP and WPA"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by samotano on 2006-09-27
I have two wireless connections: one WEP and one WPA encrypted.  I am currently connected to the WEP one, and I have no problems here. 

I now want to connect to the WPA one. However, even after installing Network Manager, it keeps displaying the "No network devices have been found" message.

I am running the latest/updated release (6.06 LTS).
Thanks to anyone who can help!
S.

---

### Post by shat on 2006-09-27
You mentioned that you were connected to the WEP one, then you tried installing network-manager: 

Were you using another tool for your WEP network before?  Or through the console?  

If you were using something else, you would need to disable your wireless card through the previous tool before moving on to network-manager.  

Can you connect to your WEP through network-manager?

---

### Post by samotano on 2006-09-27
I intially set up my WEP connection by going under:
System>Administration>Networking
and then selected my Wireless connection (wlan0), clicked on properties and adding the ESSID and WEP key.
I might have done something else, but it was a while ago and can't remember much...:( 

NO, I cannot connect to my WEP using Network Manager.  Network Mnager only displays the following messages:
-No network connection
-No network devices have been found

Thanks,
S.

---

### Post by fngaserin on 2006-10-25
Try removing all the essid and password. Apparently NetworkManager will only recognize interfaces with auto and dhcp.

---

