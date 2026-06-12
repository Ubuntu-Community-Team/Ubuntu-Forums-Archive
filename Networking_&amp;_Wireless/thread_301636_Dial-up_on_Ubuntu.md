---
title: "Dial-up on Ubuntu?"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by c0rrupt3d_fate on 2006-11-17
I need to get internet access via dial-up connection on edgy(what I'm currently using) first of all, is this even possible? and secondly, what service providers would even support such a thing as  linux dial-up? and I also need a ubuntu compatible modem :-k 


....any help comments suggestions or ideas would really be appreciated, because of my schedule, I may or may not be able to check back on this thread, so if you could send a private message my way, that would be really appreciated


Thank you, in advance

---

### Post by odin1965 on 2006-11-17
Best modem is an external. I have a USR sportster which works great. You can get a lot of winmodems to work, but my hardware modem is a lot faster over the bad phone lines that we have here.
  I have had the best luck connecting with GnomePPP (frontend for wvdial)and I believe this should be included by default. There are several other ways, see [https://wiki.ubuntu.com/SettingUpModems](https://wiki.ubuntu.com/SettingUpModems) for more info on the options.
  My provider does not support linux either, but wvdial is smart enough to connect without any modification, usually. Just enter username and password into GnomePPP.
  To get my browser and email to connect to the internet after the modem connected, I had to set the default route to the internet as the modem.

---

