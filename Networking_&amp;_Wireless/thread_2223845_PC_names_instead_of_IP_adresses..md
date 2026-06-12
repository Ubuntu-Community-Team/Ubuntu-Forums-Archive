---
title: "PC names instead of IP adresses."
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by iX9 on 2014-05-13
With KRDC or Realvnc viewer or other apps, I must input IP adresses of computers instead of PC names (on the LAN).
In M$ win I can use just names.
Is there any way how to kubuntu learn these names?

---

### Post by spynappels on 2014-05-13
You can add the names and IP addresses to /etc/hosts and this file will be used before DNS resolution is attempted.

---

### Post by iX9 on 2014-05-13
But IP adresses changes against PC names time-to-time, as DHCP "wants".
So then I must change /etc/host everytime....
Not good...

---

### Post by spynappels on 2014-05-13
Then you will need to use NetBIOS, see the following thread for help on how to set this up:

[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

---

### Post by Iowan on 2014-05-13
I have an aging machine set to run **dnsmasq** as my network DHCP server. It links names to IP addresses, so I can ping or SSH by machine name. Wish I could get the **dnsmasq** on my Tomato router to do the same...

---

### Post by iX9 on 2014-05-13
ThanX, solved.

---

