---
title: "Atheros card went missing"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by randumnumber on 2010-01-17
I have a ralink card built into my laptop, and it has gone missing. I was doing a little work with the aircrack-ng package and trying to configure my dhcpd using airbase-ng. to make a soft ap for my network. i have 2 wifi cards attached to my laptop one external one internal, after modifying the dhcpd.conf file 2 days ago i did a reboot, "i think my internal wifi card had been set to monitor mode" and my internal wifi card went missing.

I did a ifconfig -a and it was still in the system but it was unassigned. so i renamed the dhcpd.conf file to dhcpd.confnull and it worked fine after a reboot . then yesterday i was trying to continue my work and modified the dhcpd.conf file again and this morning after my laptop had restarted on its own over night (because the power cord got disconnected and it died). my card has gone missing again!!!! 

I did an ifconfig -a again and now my card is nonexistent, its not even listed in my /etc/network configuration files. i tried the same fix i had used the day before, boot to safe mode rename the dhcpd.conf file and reboot, but it didnt work.

so my question is, how can i get my network card back? i am willing to reinstall it by modifying any kind of boot files to initialize it or whatever it takes. any pointers?

---

