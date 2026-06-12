---
title: "ipw3945 WPA dont work"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by limus on 2007-04-22
When i go to network settings i don't see any option WPA, just WEP (hexadecimal) and WEP(ascii). Is there any solution to get WPA working. 

 Another problem in the network manager is after the name of a protected network i should see a shield like 

[IMG]https://wiki.ubuntu.com/7%2e04Tour?action=AttachFile&do=get&target=NetworkManager.png[/IMG]

but i don't see.

thanks and sorry for my bad English.

---

### Post by spd106 on 2007-04-24
This usually only happens when your AP is set to not broadcast it's ssid, as it also says what kind of encryption it will accept. Network Manager has trouble if it does not receive this information.

You could try creating a new network with your information instead, hopefully it will then find the AP and connect.

Good luck.

---

