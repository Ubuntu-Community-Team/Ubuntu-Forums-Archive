---
title: "[SOLVED] Odd wireless problems in 8.10 after upgrade"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by AeroGT3 on 2008-11-20
hi all,

I recently upgraded to 8.10 from 8.04 (x64). I hate upgrading because it always seems to have problems, but I hate fresh installs even more so . . .

After upgrading I had some firefox issues which I fixed. One thing I cannot figure out is this: everytime I boot into Ubuntu fresh, I cannot access my router. I can access some neighbors' pay by the hour routers, but not my own.

Now the weird part: if I boot into Windows, set up the wireless there (I can dual boot, but off different HD's), then boot back into ubuntu, it works! My wireless hooks up to my router automatically. 

I have configured the connection with MY router by graphically entering in the password. Thing is, as soon as I close the dialog the password is changed to some random crap, i.e. 134908klhbvcs9ai6

Any ideas? This is extremely obnoxious but obviously there has to be SOME fix because after a reboot from windows I can get online no problem . . .

Cheers,

---

### Post by AeroGT3 on 2008-11-21
Well,

It looks like the solution for me was to install and configure WICD:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

My problem is solved!!

---

