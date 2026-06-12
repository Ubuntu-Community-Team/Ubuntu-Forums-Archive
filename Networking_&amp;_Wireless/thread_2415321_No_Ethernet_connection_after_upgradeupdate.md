---
title: "No Ethernet connection after upgrade/update?"
date: 2019-03-24
forum: Networking &amp; Wireless
---

### Post by widert on 2019-03-24
unfortunately, my network connection is down after I did and update. 

The ethtool shows “link detected”, but no connection... :(

---

### Post by praseodym on 2019-03-24
Please run the wireless script from the sticky thread ans show the outputs

---

### Post by widert on 2019-03-25
Thanks, but unfortunately I have not installed a Desktop, and now without internet connection I guess Im not able to install one?

Also, seems like the script is wireless troubleshooting only?

---

### Post by widert on 2019-03-27
I'm a bit of an ubuntu noob and this is very frustrating. I haven't installed any desktop and without a internet connection I cannot upgrade drivers etc. Do I have to reinstall or...???

Can anyone please help? Kind of desperate since I'm running Homeseer on my server controlling lights etc at home... :(

---

### Post by houstonbofh on 2019-03-27
We need a lot more information.  What did you upgrade from and to?  Where was your network configured? (Network manager, /etc/net/interfaces netplan?)  What errors are you showing with IP? (ip neighbor, ip link, ip -s, ip -stats)

---

### Post by widert on 2019-04-02
Well, I finally figured it out, seems like it was an DHCP issue with two devices trying to connect with the same IP. Plugged everything out of my router and one and one back in and that solved it.

---

