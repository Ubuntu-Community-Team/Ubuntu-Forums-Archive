---
title: "No Iternet after installing ubuntu"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by ericsaxalto on 2007-08-30
Apparently, I didn't install 7.04 but 6.06 (Dapper Drake).  Anyhow, I can't get any internet access.  I have wireless internet at home but I can't get any access.  Firefox just tells me "Firefox can't find the server for (fill in website)".  Would it help if I just install 7.04?  I'm not sure what to do.  It definitely recognizes that there is a wireless card and the computer's wireless light is on.  I'm using a Gateway MT6705 but I do not know the make of the wireless card.

---

### Post by mlissner on 2007-08-31
Wireless cards can be quite a bear. You indeed might have better luck upgrading, though I wouldn't count on it. That said, if you're thinking of upgrading already, and just installed, you should probably just go for it in my opinion.

As for the wireless, if it's recognizing the card, you're off to a good start. Try the following code in a terminal and see what pops up:
```
lspci | grep -i network
```

If that yeilds results, you might be interested in just doing an lspci -vvv, which will show you more about your hardware than you ever wanted to know. Anyway, once you know the name of your network card, you might try looking it up and seeing what you get.

Failing that, post it here again. If you find something that fixes it, post that here too...good luck!

---

### Post by ericsaxalto on 2007-08-31
mlissner,
Thanks!  I did find out the make of the ethernet card.  I'm not sure what to do with it now except google it for info.  It said: 

Ethernet Controller: Marvel Technology Group Ltd.: Unknown device 4352 (rev14)
Subsystem: Gateway 2000: Unknown device 0366

If that means anything more to you I'll try anything.  Thanks!

---

