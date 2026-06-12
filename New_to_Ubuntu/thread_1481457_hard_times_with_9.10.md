---
title: "hard times with 9.10"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by clarkis1 on 2010-05-12
OK, so I have/had 9.10 installed and working relatively nicely (wouldn't see my USB ext HDD on another networked Windoze machine)... so I decide to upgrade to 10.04... install failed to complete. I rebooted into 9.10 again and decided to update 9.10 (not to 10.04, just an update). Updater said 1200+ files had to be updated... OK, I'll go for that. Machine hung and never completed installation. I used my 9.10 live CD to get to the results file you guys like to see for boot problems. I'll post it later. I have an Intel 945 motherboard with a Pentium D 3MHz processor, 2 GB RAM, 1 ea 200GB HDD and 1 ea 37G HDD. I have booted as far as the GRUB menu, I selecte the oldest version and it tries to recover... Do I have to install 10.04 from the 10.04 .iso and if I do, do I lose my VirtualBoxes and files that I have stored in my /home?

---

### Post by TwoEars on 2010-05-12
Run the following command from the terminal -
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
``` and post any errors you get here.

It will take a while, you have about 1GB to download, at guess :)

---

### Post by clarkis1 on 2010-05-12
TwoEars, thanks for replying... would aptitude be better for this than apt-get?

---

### Post by natravis on 2010-05-12
aptitude and apt-get are the same program, just different ways to call it (aptitude is a front end for APT).

---

### Post by clarkis1 on 2010-05-12
what's this all about and what do I do? I get a GNOME terminal window that says: 
"The following Linux command line was extracted from /etc/default/grub or the 'kopt' parameter in GRUB Legacy's menu.lst. Please verify that it is correct, and modify it if necessary.
There's a Linux command line: field and an <OK> button I can't activate...

---

### Post by natravis on 2010-05-12
That sounds like a GRUB update. I imagine if you press TAB you would be on the "okay" button. You may want to run the update for that separately to let it go then you can use the linked command above again. I'm not 100% certain on the command to update just grub by itself, but I'll post when I get home.

---

### Post by clarkis1 on 2010-05-12
thanks, natravis! I OK'd out and the next message said it was going to use quiet-splash as the default command - I said OK to that and off it went with the update!

---

### Post by natravis on 2010-05-12
Glad to hear it! Make sure to mark the thread as solved using the thread tools at the top.

---

