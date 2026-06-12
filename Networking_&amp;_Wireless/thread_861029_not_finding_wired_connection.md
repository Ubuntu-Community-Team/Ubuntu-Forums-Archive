---
title: "not finding wired connection"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by KillaW0lf04 on 2008-07-16
Hi all, im having a problem getting my laptop to detect a wired connection i use at work. At home the laptop manages to find the wireless connections no problem and even automatically connects, but at work whenever i put in the ethernet cable, nothing connects and internet wont work for me............Any suggestions on what i can do?

---

### Post by prshah on 2008-07-16
> **KillaW0lf04 said:**
> 
 at work whenever i put in the ethernet cable, nothing connects and internet wont work for me


Do you have any idea of the setup used at work? If you can get access to Windows on the work network, click start-run, type ```
cmd
``` and press enter. A black window should open up. Then give the command ```
ipconfig /all
``` Post the output here, it will give us a clue to your network setup. If for any reason you can't give out this information, then plug in your laptop, and give the output of the following commands```
sudo mii-tool eth0
sudo dhclient eth0
cat /etc/resolv.conf
ifconfig
```

Replace eth0 with the actual name of your wired network interface... though I don't think there will be any change.

---

