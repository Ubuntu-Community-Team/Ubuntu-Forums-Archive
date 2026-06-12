---
title: "Network Settings Link Missing in Xubuntu 8.10"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by appier on 2009-04-17
I just did a clean install of Xubuntu 8.10 (Intrepid Ibex) onto an older Gateway laptop.  The documentation says the path to get to the network settings is: 

Applications --> System --> Network Settings

In my installation the link is missing.  I used the Network Settings to help set up the Wifi connection with a USB adapter.  In Hardy, the link was there, and it worked fine.

Is there a package missing or a way to add the link?

Thanks,

Mark

---

### Post by mikewhatever on 2009-04-17
All network settings in 8.10 are done through the network manager. Either right click on the nm icon and select Edit Connections, or look under System->Admin->Network Tools.

---

### Post by appier on 2009-04-17
Thank you for your quick response.

Last night when I tried to configure the wireless using the Network Manager accessed via clicking the network icon in the panel, I did attempt to set up a connection manually.  However, in addition to the network name and password, it wanted MAC address, BSSID, etc.  The catch is that as I wander around at the school, the Mac address of each wireless point is different.  Gnome's Network Settings would show a list of networks and signal strengths, and would automatically log me on the network.  It may sound lazy, but I really don't want to have to manually enter all of this information every time I walk into the zone of a different access point on the same network.

Is there some way to configure the Network Manager to behave as Gnome's did?  Or, is there a way to bring in Gnome's interface and use it?

Thanks again,

Mark Appier

---

### Post by mikewhatever on 2009-04-17
Gnome network manager does show the list of available wireless networks and lets you connect to them by point and clicking. Once again, the network manager is on the top panel next to the clock. The parameters you mentioned are usually not mandatory, but if a networks requires BSSID and MAC, you'll need to acquire them in order to connect.

---

### Post by appier on 2009-04-17
I finally got home again and tried your advice.  This time it worked.

Thank you!

---

