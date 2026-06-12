---
title: "feisty network doesnt start automatically *sometimes*"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by whizbaby on 2007-07-15
Hello all,
does somebody know why in feisty my network sometimes (unpredictable) doesnt come up? I have to start a 'dhclient eth0' manually then. The network card is not the problem, because
-it worked flawless in dapper and edgy
-I get the same results if I put in a brand new card
-another machine with feisty on it produces the same error

In another feisty setup, autofs doesnt seem to come up sometimes (sometimes it does), too, leaving me homeless...(until I start it manually). /home is imported from a file server using nfs and authenticated by ldap (btw I tested that its not an ldap or server-timeout issue).

Anybody knows one of these?

---

### Post by lyckantropen on 2007-08-24
> **whizbaby said:**
> 
In another feisty setup, autofs doesnt seem to come up sometimes (sometimes it does), too, leaving me homeless...(until I start it manually). /home is imported from a file server using nfs and authenticated by ldap (btw I tested that its not an ldap or server-timeout issue).

Have/had the exact same problem. When login fails, login through LDAP couldn't be done because there was no home directory. Sometimes it worked, sometimes it didn't. I tried changing the order in which autofs started through update-rc.d, and although it failed less, it still failed quite often.

In the end I added a script to "mkdir /home" before starting autofs, and a few dozen restarts later, still no problem. I came around looking to see if anyone had a similar problem and if an appropriate explanation for deleting /home occassionally exists.

---

