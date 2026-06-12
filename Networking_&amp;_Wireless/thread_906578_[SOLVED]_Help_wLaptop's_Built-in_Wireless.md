---
title: "[SOLVED] Help w/Laptop's Built-in Wireless"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by CommanderxGreen on 2008-08-31
Using: Ubuntu 8.04 - Hardy Heron
Laptop Model: Compaq Presario C770us

I recently bought a new laptop.  I've set it up on Dual-Boot Windows Vista & Ubuntu.  It has built-in wireless support(like many laptops do these days) which works fine in Vista, but I can't seem to get it to work in Ubuntu.  I think it may have something to do with the fact that my computer has an ON/OFF button for the wireless network dealy, because it stays OFF whenever I boot in Ubuntu, and it won't turn on when I push the button.  I've poked around on Google looking for people with similar problems, but I can't seem to find anything.

I can provide additional info about the machine if necessary; I wasn't really sure what would be relevant.  Sorry.  

Help?  Thanks,
Andrew "Commander Green" Schmidt

EDIT:  Found solution in [this thread](http://ubuntuforums.org/showthread.php?t=902860).  Thanks to gabsik.

---

### Post by buu700 on 2008-09-06
Hi. I also have a Compaq C770us, but I wasn't able to get wireless working with those instructions on Ubuntu 8.04.1 amd64. What exactly did you do (and were you using i386 or amd64)? Thanks.

---

### Post by CommanderxGreen on 2008-09-06
I'm using i386.  I don't think I can offer much assistance, as I did pretty much exactly what the topic said and it worked.  :(

---

### Post by buu700 on 2008-09-06
Okay, thanks. I'll post back with the results of trying to setup wireless on i386.

---

### Post by cjsm444 on 2008-09-06
I'm thinking about getting this laptop too.  Anticipating whether the fix worked for you, buu!

---

### Post by buu700 on 2008-09-06
No luck...

---

### Post by buu700 on 2008-09-19
Good news: Under a fairly fresh install of Ubuntu SE Hardy i386, I got wireless working by following gabsik's instructions (I think last time I tried I forgot to reboot the one of the times). Caveat: the light stays orange all the time, though hopefully that will be fixed eventually (maybe not). Other than the wireless hassle, this seems to be a great *nix laptop (I actually purchased it partly because I thought it would be painless with wireless, since the ath9k kernel driver had just been announced (yes, I did try Intrepid with 2.6.27 (which includes ath9k); no dice)). If you are still looking for a laptop and you don't mind a slight hassle with wireless and not having a blue light (which does actually bother me...), this is definitely a good choice (and it has decent Intel graphics, which is awesome considering the awful quality of proprietary graphics drivers these days).

---

### Post by cjsm444 on 2008-09-20
Thanks for the update-- my boyfriend got the laptop (C770us) working fairly quickly, no major glitches for now.  He claims the "screen moves," but I see no such thing :KS

---

### Post by buu700 on 2008-10-08
By the way, the wireless card works out of the box with the ath9k driver included in 2.6.27 included in Intrepid, aside from the light always being orange.

---

