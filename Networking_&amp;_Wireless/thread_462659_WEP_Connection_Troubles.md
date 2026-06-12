---
title: "WEP Connection Troubles"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by acconrad on 2007-06-02
Ok so I'm trying to connect to our wireless network and the GNOME Wireless Assistant recognizes that the wireless network is there, but it fails to connect.  Here's my connection (the ID and password have been changed, but its basically the same thing):

name: linksys
WEP?: YES (open)
password: 1920210s4

Key index (i got this from my friend who is on Windows): 1

so under wireless assitant, i configured it with that ESSID, that password and as an open connection as opposed to shared, but whether I make it ASCII or Hex it won't connect...what gives?  How do I enter in the key index? I've been able to connect to open networks with and without WEP passwords and I haven't had problems...I know the password isn't the problem...and btw, is that a hex or an ascii password...Windows doesn't ask you to differentiate.

Any ideas?

---

### Post by chili555 on 2007-06-03
I think the password IS the problem.
# 40-or 64-bit ASCII WEP code has five characters
# 40- or 64-bit HEX WEP code has 10 characters
# 128-bit ASCII WEP code has 13 characters
# 128-bit HEX WEP code has 26 characters 

Yours has 9 characters. Please recheck the key.

---

