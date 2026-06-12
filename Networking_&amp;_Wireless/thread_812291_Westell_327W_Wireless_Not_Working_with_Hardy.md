---
title: "Westell 327W Wireless Not Working with Hardy"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by bcc21k on 2008-05-29
I recently installed Hardy on an IBM T22 laptop with a Cisco Aironet 350 wireless card and I can not connect to the wireless network. I do not see the wireless network in Network Manager screen. The Status and Activity lights on the wireless card do not flash on and off. I have a Westell Versalink Model 327W wireless modem. Is this modem compatible with Hardy? I read in the Network Manager documentation that the Aironet 350 is compatible with either unencrypted or WEP networks. I am not sure what encryption is used by the modem.
Thank you.
bcc21k is online now Report Post   	Edit/Delete Message

---

### Post by kerry_s on 2008-05-29
i have a westell, so it's compatible with linux, after all its built on linux. 

i would check your wireless settings, are you sure you setup your wireless card and it's working?

---

### Post by bcc21k on 2008-08-27
Aironet cards do not support WPA under Linux, thus you can't connect to your
WPA-enabled route anyway.  Network Manager won't show APs you cannot possibly connect to.

---

