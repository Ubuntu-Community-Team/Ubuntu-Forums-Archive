---
title: "Problems connection to wireless router"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by terio on 2007-01-25
Hello,

I am trying to connect to a wireless router and it is not working.

I have:

-Ubuntu 6.10 Edgy Eft
-Linksys WiFi card WPC54G
-ndiswrapper
-Router WRT54G

I already had it working in another location. I installed ndiswrapper and configured the connection there. 

Now, in a new location, it does not get an IP address.

ndiswrapper reports the driver installed and the hardware present. 

I set the ESSID using iwconfig, and set also the 10 digits hex key, but dhclient is unable to get an IP.

The router is set to use WEP 64 bits, and the 3rd key. That is the key I enter when configuring the card but it does not work.

I would really appreciate any help with this.

---

### Post by K.Mandla on 2007-01-26
If all you've done is moved the machine to a new location, it's possible there's some sort of interference that's preventing it from validating. 

By the way, you don't have a baby monitor, do you? Supposedly some baby monitors work on the same frequencies as wireless connections, and they'll garble each other.

---

### Post by terio on 2007-01-26
Hi, thanks for your answer.

The new location is actually another house with a different network and router. The router is the linksys I specified previously. 

It should not be related to interference. Other laptops with Windows XP work perfectly from the same spot. 

Besides, iwconfig reports bad encryption packets received. So, I guess it is a matter of setting up the wep encryption correctly. I have tried ascii, hex, different keys (of the set of 4 that the router produces) but nothing works.

---

### Post by K.Mandla on 2007-01-26
I would turn off the encryption briefly and see if you can simply connect and validate across an open network. If it's working, then restart your encryption and maybe you'll spot an error.

---

