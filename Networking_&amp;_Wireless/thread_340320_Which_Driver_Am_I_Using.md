---
title: "Which Driver Am I Using?"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by Echam Tusk on 2007-01-17
Is there an easy way to tell which driver my ipw2915 is using. I'm trying to get connected to my WPA-PSK encrypted network. Unsecured is no problem. A couple of the posts I've tried to follow require the driver as part of the command. Total n00b please excuse the ignorance. Any help much appreciated.

---

### Post by hal10000 on 2007-01-17
Open a terminal window (Apps--->Terminal) and try [COLOR="Red"]lsmod | grep ipw[/COLOR] and post the output.

---

### Post by spd106 on 2007-01-17
Try the wext driver first, then if unsuccessful try the ipw driver.

---

### Post by namaste on 2007-01-17
See [http://www.ubuntuforums.org/showthread.php?t=332857](http://www.ubuntuforums.org/showthread.php?t=332857). It shows how to use the lshw command to see which driver your wireless is using.

---

### Post by Echam Tusk on 2007-01-18
Thanks a lot. Now up and running.

---

