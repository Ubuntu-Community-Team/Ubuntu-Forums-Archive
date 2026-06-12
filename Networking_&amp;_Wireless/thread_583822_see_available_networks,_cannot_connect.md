---
title: "see available networks, cannot connect ?"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by geetlord on 2007-10-20
I have just upgraded to gutsy after much trouble, however now, my usb linksys 802.11b wireless card wont let me connect to available wireless networks. It previously worked out of the box in feisty, so Im not sure what has changed. I can see my network, and can select a network to connect to, however the connection always fails. where do i even start in trying to fix this?

---

### Post by ts2000 on 2007-10-20
I had the same issue.  I fixed it by going to bed and getting some sleep.  Upon waking up in the morning I setup 'manual' connect with my static settings.  I found the network then connected, although, the panel applet shows no connection.

---

### Post by geetlord on 2007-10-20
i just managed the same thing more or less: I had to dhconfig wlan0 after connecting to my network, but it works now, thanks!

---

