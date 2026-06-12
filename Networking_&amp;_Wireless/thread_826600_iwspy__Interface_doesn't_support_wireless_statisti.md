---
title: "iwspy  Interface doesn't support wireless statistic collection"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by dnaxx on 2008-06-12
Hello,

I want to gather link information (e.g. signal quality) between all nodes in my ad hoc wireless network. But when I run iwspy (ubuntu hardy), I get this message: "iwspy  Interface doesn't support wireless statistic collection". 
Is there a way to overcome this problem? I am using the standard WLAN drivers for Intel Centrino 2 wireless cards.

Regards,

---

### Post by vnshng on 2008-06-16
couldn't you just 

$ crontab -e
and add " /5 * * * * iwconfig wlan0 | grep Link >> linkquality.log "
then ctrl+x y to exit and save
then it should create a file called linkquality.log with 
Link Quality=91/100  Signal level=-40 dBm  Noise level=-75 dBm
and then add a new line every 5 min

---

### Post by dnaxx on 2008-06-17
no, because I do not  need the overall link quality (which is returned by iwconfig / iwlist) but the link quality to each ad-hoc peer.

---

### Post by dejavuu on 2008-11-12
I have the same problem...
But i don't know if there is a problem with wireless card drivers...
My card is ipw2100..

---

### Post by Bladerunner_1989 on 2011-09-12
Hi, so did you get around that anyway? Just wondering as I am experiencing the same problem with atheros 5k. Moreover, I try to specify ip address or mac address for the interface but it still doesn't work (says that operation is not supported, interface doesn't accept addresses). There is also no entry for the interface in /proc/net/wireless Currently, considering that libpcap will do the trick.
Cheers.

---

### Post by jbowman on 2011-12-02
I hate to resurrect old threads but a solution for this was not posted, and it is the top google search result for what I need. :)

Did you ever get this figured out?

---

### Post by druca on 2012-03-05
[http://ubuntuforums.org/showthread.php?t=1165815](http://ubuntuforums.org/showthread.php?t=1165815)
See this thread.

---

