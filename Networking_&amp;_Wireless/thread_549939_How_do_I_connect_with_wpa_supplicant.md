---
title: "How do I connect with wpa_supplicant?"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by Genecks on 2007-09-13
I've been reading and reading and reading. I've found some information about connecting to a wireless network with Ubuntu Feisty, but I haven't been able to get everything correct. I've learned I need to use wpa_supplicant, because I'm using a broadcom card with ndiswrapper.

I've got two papers in front of me. One is for Apple, the other is for Windows XP.
I'm using Linux.

I've got these following criteria for the wireless network:

- WPA
- Protected EAP = EAP (WPA Enterprise? I think that's what it's called for apples)
- Data Encryption = TKIP
- Do not authenticate as computer
- Do not authenticate as guest
- Do not validate server certificate

1. username = user456
2. password = q120983*

The Domain part is what is getting me.
I don't quite understand it.

For XP, it says when a dialog bubble appears over the wireless connection icon, i'm suppose to type NIUNET as the domain.

For apple, inside of Tiger, the username looks like this:

NIUNET\q120983*

I noticed it includes the domain for that.
I read some stuff for wpa_supplicant, and none really referred to the domain option.

How do I set this up?

---

### Post by Genecks on 2007-09-13
Any takers?
*bump*

---

