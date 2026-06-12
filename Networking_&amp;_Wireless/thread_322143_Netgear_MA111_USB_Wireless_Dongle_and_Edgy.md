---
title: "Netgear MA111 USB Wireless Dongle and Edgy"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by MuWarriors on 2006-12-20
New to Ubuntu this week, so bare with me...
Does anyone have the Netgear MA111 Wireless working with the Edgy release?  I have tried following other guides, but I get lost somewhere along the way.  

I have looked at the [https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111) page, but it only has Breezy and Dapper support. 

Also, I get errors when attempting to do a lot of the terminal commands.  

Can anyone help me out?

Thanks in Advance

---

### Post by mengfei on 2007-03-01
Hi there!

All I did is

sudo apt-get install linux-wlan-ng

to install it under Edgy.

And then I did

sudo apt-get install network-manager network-manager-gnome

to install the wireless manager.

My usb dongle now sees the networks and such...

but so far I haven't had any luck connecting to any.

Then again, I'm not connecting to your everyday wireless networks, and I haven't really given it multiple tries yet, so who knows, this may work fine for you.

Hope that helps!

---

