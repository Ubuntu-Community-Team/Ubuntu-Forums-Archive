---
title: "Macchanger Will Not Work In 14.04"
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by coljohnhannibalsmith on 2015-07-22
Hello,

I have not been able to get macchanger to work in 14.04.  Here is the terminal output:

[sudo] password for sophie: 
Current MAC:   a4:ba:db:c4:73:bc (Dell Inc.)
Permanent MAC: a4:ba:db:c4:73:bc (Dell Inc.)
New MAC:       a4:ba:db:c4:73:bc (Dell Inc.)
It's the same MAC!!
Current MAC:   78:e4:00:44:49:59 (Hon Hai Precision Ind. Co.,Ltd.)
Permanent MAC: 78:e4:00:44:49:59 (Hon Hai Precision Ind. Co.,Ltd.)
[ERROR] Could not change MAC: interface up or insufficient permissions: Too many open files in system

BTW, I always disable networking before running this.


Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-07-24
Bump.

---

### Post by CantankRus on 2015-07-28
This maybe...
[**_[COLOR="#B22222"]macchanger bug[/COLOR]_**]("https://bugs.launchpad.net/ubuntu/+source/macchanger/+bug/1316278")

---

### Post by coljohnhannibalsmith on 2015-07-28
Thank you. I saw the bug; so I tried the following:

sophie@sophie-Inspiron-1545:~$ sudo macchanger --mac=78:e4:00:44:49:58 wlan0
Current MAC:   78:e4:00:44:49:58 (Hon Hai Precision Ind. Co.,Ltd.)
Permanent MAC: 78:e4:00:44:49:59 (Hon Hai Precision Ind. Co.,Ltd.)
[ERROR] Could not change MAC: interface up or insufficient permissions: Too many open files in system
sophie@sophie-Inspiron-1545:~$ 

It looks like the MAC did change from 59 to 58; but I still get the error msg.  At least half the battle's won.

Hannibal

---

### Post by coljohnhannibalsmith on 2015-07-28
I love macchanger.  I have a lot of fun with it.  I sometimes sit in a coffee shop that
restricts their WiFi use to only two hours, then run macchanger, delete the store's cookie
from my browser and log back on as if I had just come in.  It doesn't get any better!

BTW, I've written the following little script that automates macchanger and run's in a terminal;
so I can just run it from the desktop.  All I have to do is enter my root password.  I also changed
the icon to a Big Mac:

```
#!/bin/sh

#sudo /etc/init.d/networking stop

sleep 4

sudo macchanger --mac=a4:ba:db:c4:73:bd eth0 #-r eth0

sleep 4

sudo macchanger --mac=78:e4:00:44:49:58 wlan0 #-r wlan0

sleep 4

#sudo /etc/init.d/networking start

sleep 4
```

Does anyone know what characters I need to use to force a CR/LF?  I thought it was \n; but I recall
that didn't work from within my script in 12.04; so I just did without.  I did have it working in an earlier
distro and it made the terminal output look really nice.  If anyone can make some suggestions for improving
this script I'd be very grateful.

Hannibal

---

