---
title: "Policykit-help please"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by eBus37 on 2009-01-03
Hi roomies....I uninstall the policykit due to asking me for a password I did not set. I'm the only user of my pc. After a normal reboot and at startup my keyboard and mouse are disable and I'm not able to log in. The pc is running fine, but I'm not able to started it or to log in due to not having keyboard or mouse.

Is there a way to resset it or re-install the polikit? is there a restore back to certain date like xp? Please let me know asap.

Thank you

---

### Post by meindian523 on 2009-01-03
Boot into recovery mode and do ```
apt-get install policykit
```

---

### Post by eBus37 on 2009-01-03
> **meindian523 said:**
> Boot into recovery mode and do ```
apt-get install policykit
```


How do I get to recovery mode? My pc bootsup but it stopped at the log in screen.

Thanks

I GET THIS ERROR MESSAGE:: [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) intrepit/main policykit 0.9-1ubuntu3 could not resolve de.archive.ubuntu.com

failed to fetch [http://de.archive.ubuntu.com/ubuntu/pool/main/p/policykit/policykit_0.9-1ubuntu3_i386.de](http://de.archive.ubuntu.com/ubuntu/pool/main/p/policykit/policykit_0.9-1ubuntu3_i386.de)

---

### Post by meindian523 on 2009-01-03
Reboot by pressing the Reset button,and when the screen shows Grub stage 1.5(or stage2,I don't remember off the top of my head)the countdown starts 3...2....1..0,press Esc,then select Recovery mode and press Enter.And your error is probably because it's intrepi**d**,not intrepit,unless that is a typo you committed while posting.

---

### Post by eBus37 on 2009-01-03
> **meindian523 said:**
> Reboot by pressing the Reset button,and when the screen shows Grub stage 1.5(or stage2,I don't remember off the top of my head)the countdown starts 3...2....1..0,press Esc,then select Recovery mode and press Enter.And your error is probably because it's intrepi**d**,not intrepit,unless that is a typo you committed while posting.

Yes, it was a typo...sorry. I'm at the Sudo and I have tried to install (policykit) but I get the same failer on top. I don't know what to do. I will be hanging around till I fix the problem. Or is there a restore-set back like win-xp?

---

### Post by meindian523 on 2009-01-03
No System Restore,unfortunately.All I can say is this should act as a lesson to be careful with what you do with sudo.Could you boot into Recovery mode?

---

### Post by eBus37 on 2009-01-03
> **meindian523 said:**
> No System Restore,unfortunately.All I can say is this should act as a lesson to be careful with what you do with sudo.Could you boot into Recovery mode?

YES, I'm there now and waitng to solve my problem. I was not able to re-installed policykit, as noted on top.

---

### Post by meindian523 on 2009-01-03
ah,well.Then the best way is to change the server it attempts to download the package from.
Do
```
vim /etc/apt/sources.list
```
This will open a file.
Press i and replace all [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) intrepid ....... with
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid ..........
Press Esc and then type ```
:wq
``` to save and close the file.
Do
```
apt-get update
```
and 
```
apt-get install policykit
```
You don't need sudo,because you are already superuser.

---

### Post by eBus37 on 2009-01-03
Thanks for the quick reply and I having trying to work it out. But i'm getting a messege that is not supported and I don't get to that point were I typed in the (I)and then the address you gave me.

Q? is there a way to disable my password account from the Root@desktop? cause i'm able to get there and I'm thinking that if is disable, then my PC will finished booting up completly. Thnks

---

