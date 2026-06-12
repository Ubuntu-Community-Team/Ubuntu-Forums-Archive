---
title: "WPA and the Keyring"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by T8y8 on 2006-08-07
Ubuntu 6.06
Intel 2915 ABG, running under the 1.1.3 drivers

I followed the guide to install Network Manager and WPA, from here on the forums.

It's been working fully functional for weeks. I log in, it askes for the password to unlock the keyring, and I connect to my network.

Now however, it asks me for the WPA key every time I log in.

I ran nm-applet from the terminal, and it spat out the error that it can't save to the keyring.

Someone on IRC recommended I delete ~/.gnome2/keyrings, I did.

I downloaded gnome-keyring-manager as well, and deleted the unused keys, hoping it would save them again.

I'm out of ideas. I don't want to enter/copy-paste my 63 character WPA key everytime I log in.

I thank you for any hep in advance, and am ready to provide any output you need.

---

### Post by T8y8 on 2006-08-08
Update: After several reboots, I decided to disable cgwd on a whim. I logged back into the network, and it asked me to unlock the keyring, and now all is well

I don't know if it was a fluke, but it seems gnome-keyrings doesn't play nice with cgwd.

---

