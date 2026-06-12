---
title: "Dell Wireless 1505 Wireless-N Mini-card Not working"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by searayman on 2008-07-14
I have a new dell I just installed ubuntu on and I have this wireless card:

Dell Wireless 1505
Wireless-N Mini-card 

and it doesnt work, any help would be great!

---

### Post by tati on 2008-09-19
Seconded.

---

### Post by Ayuthia on 2008-09-19
I just did a quick search on this card and it looks like it is a Broadcom 4328 card.  If that is the case, you could try:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Or you can go with the Broadcom drivers also:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)
This link will tell you how to download the wl driver and install it.  

If you do have a wired connection and have no problems with using a test kernel, you can use this link:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Before you try this, you will want to go into the Terminal and type:
```
lspci -nn
```and see if the card shows that it is a Broadcom 4328 card.

---

### Post by tati on 2008-09-19
It is a Broadcom 4328 and your first link made the wireless work, thanks!

---

### Post by abbot on 2008-10-06
> **Ayuthia said:**
> I just did a quick search on this card and it looks like it is a Broadcom 4328 card.  If that is the case, you could try:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

beautiful.  this worked for my card.  

make sure you do the 'Hardy Bug Fix' if you're using hardy.  my module in this step was e1000e instead of ssb so i just swapped that whenever it was mentioned in the code.

---

