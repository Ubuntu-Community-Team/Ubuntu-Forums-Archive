---
title: "Strange autoconnect problem"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by pvrsnarayana on 2008-02-10
I am facing a strange auto connection problem to my wireless network.  I am connecting to a wireless network with wep authentication using nm-applet.  I stored the credentials, and until some time back it used to auto-connect without any problem.  Now, when I select the ssid from the drop down list it refuses to connect.  However when I manually connect (using connect to other wireless network) and enter the credentials, it connects.  Any ideas how to rectify this?  may be i should delete the default profile?  if so, where are the profiles stored for nm-applet?  Any help is greatly appreciated.

---

### Post by soro2005 on 2008-02-10
The profile is in ~/.gconf/system/networking/wireless/networks 

You can navigate there if you go to your home folder, make hidden files visible (ctr+h), and then follow the path above, starting with .gconf. It should work if you just delete the folder within networks that bears the name of the network you're not connecting to any more.

---

