---
title: "Dell Inspiron WiFi hard blocked issue"
date: 2015-09-10
forum: Networking &amp; Wireless
---

### Post by diegomrosa on 2015-09-10
Just for the record,

I have recently installed Ubuntu 15.04 on a Dell Inspiron 14 3000 series l14-3442-B10. It turns out that WiFi was not working and Ubuntu was showing a message saying that "WiFi was hard blocked". After trying many suggestions from the Web, what ended up solving my problem was blacklisting dell-rbtn module:

sudo nano /etc/modprobe.d/blacklist.conf

Add the following line:

blacklist dell_rbtn

Anyone else with the same problem? BTW, laptop airplane mode hot key was not working even before or after the blacklisting.

Hope that helps. Enjoy!

Diego

---

