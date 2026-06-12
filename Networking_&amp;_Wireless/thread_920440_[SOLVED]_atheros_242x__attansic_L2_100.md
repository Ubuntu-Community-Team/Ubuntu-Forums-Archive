---
title: "[SOLVED] atheros 242x / attansic L2 100"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by space-cake on 2008-09-15
hi guys, 

here's my problem. iwconfig shows that i have no eth0, as it lists only lo. lspci says i have 2 ethernet controllers, an atheros ar242x 802.11abg wireless adapter and an attansic L2 100 ethernet adapter. i can't get both of them running.

any ideas?

---

### Post by IndyGunFreak on 2008-09-15
The Atheros Device, is pretty easy to configure, if you can install build-essential.  I've never had much luck installing BE w/o an internet connection, maybe someone else can help you with that.

Are you using 32 or 64bit?  If 32bit, Madwifi seems to be the way to go... 64bit, I think you'll have to use ndiswrapper.  I never had much luck getting this to work in 64bit, so you're on your own there.

Post #7 is the one to read for 32bit, 
[http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)

but the link to madwifi is dead, but here's a link to the file you need... Just download from here and follow the instructions in post #7.

[http://rapidshare.com/files/145480697/madwifi-ng-r2756_ar5007.tar.gz.html](http://rapidshare.com/files/145480697/madwifi-ng-r2756_ar5007.tar.gz.html)

Dunno about your sound, but I'd try asking in the appropriate forum, and give them your lspci output.

IGF

---

### Post by space-cake on 2008-09-17
first of all, thanks for the reply.

i'm running a 64bit ubuntu.
i've already tried installing madwifi, but it won't complete the installation process because of some error. at some point, after downloading and installing the restricted modules from the synaptic manager, eth0 disappeared completely, meaning it's there obviously, but ubuntu won't recognize it.
i'm looking for the correct linux drivers for my card, but to no avail so far.

---

### Post by IndyGunFreak on 2008-09-17
> **space-cake said:**
> first of all, thanks for the reply.

i'm running a 64bit ubuntu.
i've already tried installing madwifi, but it won't complete the installation process because of some error. at some point, after downloading and installing the restricted modules from the synaptic manager, eth0 disappeared completely, meaning it's there obviously, but ubuntu won't recognize it.
i'm looking for the correct linux drivers for my card, but to no avail so far.

Eh, sorry, 64bit I don't have a clue.  Supposedly Ndiswarapper works, but as I said earlier, I had zero luck w/ it.  32bit however, works fine w/ madwifi.

IGF

---

### Post by space-cake on 2008-09-20
is it possible to partially reinstall ubuntu, i.e. to install only the files i need to get the eth up and running again?

---

### Post by space-cake on 2008-09-20
i solved it. kind of.

it seems that i have installed restricted modules that have been "fighting" with each other, 2.6.24-16, -18 and -19 altogether (?!). now the eth is back and the only problem now is my wireless.

---

### Post by space-cake on 2008-09-22
solved.

madwifi works also on a 64it ubuntu. this [thread]("http://ubuntuforums.org/showthread.php?t=902860") helped me.

cheers.

---

