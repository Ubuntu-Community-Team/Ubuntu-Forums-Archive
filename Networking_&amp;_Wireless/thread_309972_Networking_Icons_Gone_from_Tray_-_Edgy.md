---
title: "Networking Icons Gone from Tray - Edgy"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by Dominicus on 2006-11-30
Loaded Ubuntu 6.10 Edgy on an older notebook PC (PIII-700Mhz).

I guess I should consider myself lucky...my old Wireless PCMCIA LAN card worked (Older D-Link DWL-650 802.11b).

I loaded the Network Manager app and for a single session enjoyed the tray icons that showed the signal strength %, and could click and switch to connect to my neighbor's router and back to mine...sweet.

Now when I boot up, I get a connection, but the icons no longer appear in the tray.

How can I get these to load in every boot?  Thx!

---

### Post by drphilngood on 2006-11-30
Select:

System -> Preferences -> Sessions

Click on the ¨Startup Programs¨ tab and add nm-applet.

Hope this helps!

edit:
Here is a relative guide:

[Network Manager with WPA]("http://doc.gwos.org/index.php/Network_Manager_with_WPA")

down at the bottom in the ¨Conclusion¨ section.

---

### Post by Dominicus on 2006-11-30
Went to the Startup Tab and found I already have the following entry:
nm-applet --sm-disable

Should I remove and re-create without "--sm-disable" option?

Thanks!Dominicus

Updated: I right-clicked on the "Network Connection" systray icon and noticed it was displaying the status of the loopback 'lo' connection.  Once I changed to 'eth1' (which happens to be my wireless pcmcia card), I got the additional wireless status icons.

Problem solved...

---

