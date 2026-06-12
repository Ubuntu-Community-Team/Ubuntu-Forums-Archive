---
title: "no pptp vpn will work, how to reset pptp vpn?"
date: 2015-04-24
forum: Networking &amp; Wireless
---

### Post by ubto66 on 2015-04-24
Ubuntu 14.04 64bit
 network manager
 vpn connections
 

 I have used different pptp vpn providers. You enter server, username and password. From time to time the pptp vpn works. Now none of them works.
 I have deleted all pptp vpn connections in the network manager. Can I somehow make a complete reset of everything about the pptp? Are there files I can remove?  
 Can it be something about the 802.11 wifi connections between the computer and the router 
 device? Thank you.

---

### Post by michi1983 on 2015-04-24
Do you have any network issues? 
When you deleted all the profiles in network manager, you should be good if everything else is running fine.

---

### Post by ubto66 on 2015-04-26
My router pc connection is fine, both wifi and lan cable. I am not aware that I have made some new settings that should stop pptp from connecting.

If I fx use vpnbook the pptp vpn option, it will not work. I got one us open vpn to work, if run in terminal. Therefore it could be some error in a file in the network manager. To my knowledge the network manager files are located in etc/ppp. I do not know about the files and if any, I can remove.

---

### Post by michi1983 on 2015-04-27
Well if you don't have any network issues I would just leave everything like it is.
If you wanna be sure you could uninstall the network-manager at all which hopefully also deletes all the profiles you created and then reinstall it.
But you gotta be fit in handling /etc/network/interfaces file then, so be careful about that.

---

