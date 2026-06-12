---
title: "no-ip and thier client or dyndns and ddclient"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by ronaldor9 on 2007-11-21
which is teh better and which do you recomend i heard that no-ip is easier to set up
but is it better or the exact same

btw i need one that is able to update ip from the web

---

### Post by kevdog on 2007-11-21
I use noip -- I dont know if its better, but it has a DUC along with a web updater.  The web updater sometimes takes up to 5 minutes before you can see the change.  Ive had no problem with their service.

---

### Post by ronaldor9 on 2007-11-22
intresting you cant confiugre it to check lets say every 300 seconds beaucse i belive in ddclient you can specify this

---

### Post by kevdog on 2007-11-22
Ive never used the Linux DUC -- I wrote my own perl script to do the updating -- however I think in the Windows DUC the minimum update interval is every 5 mintues or 300 seconds.  All the sites like dynds and noip, and others use basically the same updater client with I believe just a few things that are different.  The admin at NoIP helped me write me own perl script -- it took a while.  I should have just began with the general source code and actually used this as my reference.

If the noip DUC is aone time updater command line statement (have to execute the binary everytime you want to update your date), possibly its meant to be run by a cron daemon, where you can physically control how often it updates (down to every minute if you wanted too!)

---

### Post by ronaldor9 on 2007-11-22
i under stand i kind of lost you on the last line so your saying it is possible to configure the DUC to update every minute if so how

beacuse right now im using dyndns for my ftp

and im going to use no-ip for my web site beacuse it has an option for blcoked port 80 isp which is essential

is it poosible to have more one website hosted to the same ip ? or is there a limit

thank you very much

---

### Post by kevdog on 2007-11-22
Its possible to run 2 or more websites from the same machine, depending on how you configure Apache.  I did this once but I dont remember how.  You will need to search the forums or google.

You need to tell me about the duc for noip.  Is it a command line program, or a daemon process that runs in the background?

---

