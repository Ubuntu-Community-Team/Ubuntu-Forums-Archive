---
title: "System responds slowly if not connected to network"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by amitst on 2007-04-10
Hi,

My laptop has static IP address. If I am not connected to LAN then it takes significantly more time to boot up (2-3 minutes). Also it takes 2-3 minutes to start any application. The speed comes back to normal after I plug in the network cable.

Similar behavior is observed if I connect my laptop to a different network where the network configuration has to be changed.

---

### Post by aa.ivanov on 2007-04-10
You need to deactivate the network interface whenever no cable is connected. Otherwise you're running in the problem described by you. 
Windows XP is able activating/deactivating the connection whenever you bplug/unplug the cable. Linux is not activating/deactivating network interfaces by default, though I think there are some solutions to acheive such functionality.
My personal solution is to use NetworkManager to connect whenever I don't need to manualy assign an IP address. For all my static IP addresses I have created profiles, so I can easily change them from the Administration > Network menu.

---

### Post by amitst on 2007-04-10
How do you maintain different profiles?

If I go to System -> Administration -> Networking I see an edit box called "Location". But unfortunately it is not editable.

---

### Post by amitst on 2007-04-11
Got it! I can click the 'save location' button and it asks for the name. Thanks.

---

