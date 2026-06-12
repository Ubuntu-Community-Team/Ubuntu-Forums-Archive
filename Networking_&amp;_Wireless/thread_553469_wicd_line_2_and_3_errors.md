---
title: "wicd line 2 and 3 errors"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by tmasboa on 2007-09-17
Hello, I did the graphical installer and it installed ndis for my broadcom chip (it said not supported and to use the ndis)
Anyway, I installed it, clicked System->Network and put my stuff in the wireless one (wep) but it doens't work.

SO anyway I decided i needed wicd because it has a cool name.

Used the same installer, and it isntalled wicd. The problem is when I start wicd i get:
> daniel@daniel-laptop:~$ sudo wicd-tray
Password:
/usr/local/bin/wicd-tray: line 2: cd: /opt/wicd/: No such file or directory
/usr/local/bin/wicd-tray: line 3: ./tray.py: No such file or directory


Please help! Thanks

---

### Post by kevdog on 2007-09-17
The tray.py executable should be as you suggested in /opt/wicd/tray.py

Possibly something went awry???

Do this to see where it is installed:

sudo updatedb
locate tray.py

At least that will tell you where the executable is.

---

### Post by tmasboa on 2007-09-18
Lol thanks for reply

Direcotyr /opt/wicd doesn't exist
 and

locate returns nothing

I"ll try reinstalling and post again

---

### Post by tmasboa on 2007-09-18
COOL BEANS!! (ubuntu beans)

wicd is the ownage man i installed it from synaptic no probs whatsoever

it shows my network and connected!!!!!!!

---

