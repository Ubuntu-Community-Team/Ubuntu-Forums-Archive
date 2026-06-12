---
title: "NFS share issues"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by Christilut on 2007-12-09
Hey,

I'm having some problems with my NFS shares in my network. The problem is not that i can't access it, but every time i either reboot or change my network connection on my laptop from wired to wireless or vice versa, i have to run '/etc/init.d/nfs-kernel-server restart' on the nfs server and then 'mount -a' on my laptop. 
It works and all but its kinda tedious doing this several times a day.

I just reinstalled gutsy yesterday and the problem is still the exact same, so i'm guessing it lies on the server (not really a server, just an old pc also running gutsy).

This is what i'm using on my server:
/etc/exports:
/tv/ alphatop(rw,no_subtree_check)

And on my laptop:
/etc/fstab:
alphavast:/tv/ /home/alpha/TVvast/ nfs defaults 0 0


Any way to make this a little easier?

---

### Post by Christilut on 2007-12-10
Bump

---

### Post by Craigus on 2007-12-10
what happens if you specify the server IP address instead of [COLOR="Blue"]alphavast[/COLOR]  ?

---

### Post by banewman on 2007-12-10
From reading different howtos I ended up using - 
192.168.1.2:/media/ww20b/ /filem nfs rw,hard  0  0
Hope it helps. :)

---

### Post by Christilut on 2007-12-10
I tried both but no change :(

---

### Post by Christilut on 2007-12-11
Bump

---

### Post by LuisC-SM on 2007-12-11
Here is a brilliant howto:
[http://ubuntuforums.org/showthread.php?t=249889&](http://ubuntuforums.org/showthread.php?t=249889&)

Cheers

Luis

---

