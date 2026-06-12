---
title: "Reconfiguring dhclient on boot"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by KelliShaver on 2007-09-02
Hi, folks.

I have an old Dell Inspiron notebook running Ubuntu and i'm using a PCMCIA card that has a  RT2500 chipset. I got everything installed and working smoothly thanks to [url=http://ubuntuforums.org/showthread.php?t=9454
]this wonderful tutorial[/url]. However, every time I reboot the laptop I have to open up a terminal window and issue the command 'sudo dhclient wlan0' before the card will work. 

This isn't a big deal, but I was just wondering, is there any way I can automate this/make the change permanent so that I don't have to do it each time I boot up?

Thanks!

---

### Post by eggdeng on 2007-09-02
```
sudo gedit /etc/init.d/rc.local
```

Paste the line ```
dhclient wlan0
``` just under the opening #! /bin/sh. Save & reboot.

---

### Post by noob12 on 2007-09-02
Could you post the output of this?
```

cat /etc/network/interfaces

```

---

