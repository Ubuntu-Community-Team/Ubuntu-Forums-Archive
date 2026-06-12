---
title: "NetworkManager always chooses neighbor's wireless!"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by fizgig on 2007-02-19
Subject pretty much says it all.  Only thing that might be useful to know is that my network has a WEP password requiring me to enter my keyring password.

I guess networkmanager doesn't like waiting for me to give the keyring password and just joins the neighbor's unencrypted network.

Any help appreciated.

---

### Post by spd106 on 2007-02-19
Network Manager will only automatically connect to networks it has connected to previously. It stores this information in gconf for those using GNOME (not sure about kde).

You can see the network profiles in .gconf/system/networking/wireless/networks/ and remove unwanted networks through gconf-editor.

---

### Post by fizgig on 2007-02-19
Thanks!  I was able to see the networks in gconf-editor but I wasn't able to delete any.  But, I went to the directory you mentioned and say my neighbor's network there and was able to delete it.  Now when I boot up it connects to my AP (after getting my keyring password).  Yay!

---

