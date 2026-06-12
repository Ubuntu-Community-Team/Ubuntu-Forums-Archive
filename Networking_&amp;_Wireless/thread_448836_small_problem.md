---
title: "small problem"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by xtang on 2007-05-19
if i connect / turn in my Ethernet modem/router which is connected to the internet whilst xubuntu is running, it does not seem to detect the router and thus will not access the internet unless i leave it alone for 5 minutes. However, if i reboot, xubuntu seems to detect it properly and the internet works fine straight away.

This is annoying because i often only switch on my router when i need to  (i dont leave it always on)

thanks for any help

---

### Post by sdide on 2007-05-19
perhaps (as root or with sudo)

~# dhclient eth0

will help. 
(replace eth0 with the relevant interface if neccesary)

---

### Post by xtang on 2007-05-20
thanks, but what does that do?

---

### Post by Kobalt on 2007-05-20
It will restart the dhclient and make it connect to your router. 
If you don't want to do this in command line you can use Network-Manager (it's in the repos and can be used under XFCE as well). Launch it with ```
nm-applet
```

---

