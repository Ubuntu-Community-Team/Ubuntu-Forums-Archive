---
title: "Got RT2500 working with roaming"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by pclark36 on 2007-10-12
After much trial and error, I've got my RT2500 card working.   Apparently it's not a problem with the Feisty driver, it's NetworkManager.  I uninstalled it, and installed GTKwifi, and it works like a champ!

[http://gtkwifi.sourceforge.net/](http://gtkwifi.sourceforge.net/)

---

### Post by madmatrixz3000 on 2007-10-12
I am unblacklisting right now and trying again, from a fresh install do I just have to install GTKwifi or is there other stuff

---

### Post by drbob07 on 2007-10-12
I can second that it was a problem with Network-Manager.
I disabled it, and manually configured the card without a GUI.

However I have given up on encryption and use Mac Filtering, which solved my problem anyways ;).

---

### Post by pclark36 on 2007-10-13
> **drbob07 said:**
> I can second that it was a problem with Network-Manager.
I disabled it, and manually configured the card without a GUI.

However I have given up on encryption and use Mac Filtering, which solved my problem anyways ;).

All I had to do was uninstall NetworkManager, install Gtkwifi.  I am using WEP encryption with a non-broadcasting router and it works fine :)  Finally no PCMCIA card sticking outta my laptop!

---

