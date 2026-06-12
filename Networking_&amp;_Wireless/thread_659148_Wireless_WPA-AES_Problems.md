---
title: "Wireless WPA-AES Problems"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by mtdewulf on 2008-01-05
I am trying to move solely to using Linux on my laptop (right now I dual boot on both my laptop and desktop).  One of my biggest problems at the moment is getting my laptop to connect to my home network which uses WPA w/ AES encryption.  I can connect fine under Windows.  

When I try to connect under Gutsy, I am asked for a password that I enter correctly, however the connection never works.  I am puzzled as to why this is? After some research, I see that I may need to setup a wpa_supplicant file to get this to work.  Also, it seems that I need to use PSK encryption instead of AES.  I would prefer not to use the wpa_supplicant file because I like to take my laptop to coffee shops and use it there from time to time.  I don't want to have to mess with a script every time I enter a new network area.  Also, I am hesitant to move from AES to PSK because I have many computers on my network and have never had any problems before.  I'd rather not screw with it now.  

Is there any hope for me?

Also, if it matters, the firmware on my Buffalo router is Tomato 1.07.

Thanks,
Mike

---

### Post by ubutufan on 2008-01-06
Try using Wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) instead of Network Manager.
That should solve your connection issues.

Note that Wicd will remove Network Manager during installation. And read the instructions on their site especially those configuring the /etc/network/interfaces file

---

### Post by mtdewulf on 2008-01-06
Thanks!  Wicd works great!

---

