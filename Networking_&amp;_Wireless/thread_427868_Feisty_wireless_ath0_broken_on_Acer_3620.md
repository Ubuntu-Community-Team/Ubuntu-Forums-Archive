---
title: "Feisty wireless ath0 broken on Acer 3620"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by wagdog on 2007-04-29
I searched the forum and couldn't find a similar problem so here goes:

I upgraded from dapper>edgy>feisty all in one sitting.  When I was in dapper my wireless (ath0) worked fine.  Now that I'm in feisty the wireless no longer works (kernel 2.6.20).  If I reboot using the 2.6.15 kernel (I think that's what I was using in dapper) the wireless works again (although I have other problems which prevent me from using that kernel all the time).

Also, I'm showing a strong signal strength when I check the ath0 status but I can't connect to anything including the router.

How can I get the 2.6.20 kernel to work with my wireless?  

Thanks!

---

### Post by pleurastic on 2007-05-07
I fixed mine by following the instruction on [http://ubuntuforums.org/showthread.php?t=202834&page=41](http://ubuntuforums.org/showthread.php?t=202834&page=41)

Search for corax and you will see a note in red.  I removed the line suggested in the post and immediately was back on line.

---

### Post by wagdog on 2007-05-09
Thanks pleurastic but I don't even have that line (nor any wpa lines) in my interfaces file.  Hmmm, I guess I'm still on the hunt.

---

