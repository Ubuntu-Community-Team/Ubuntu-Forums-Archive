---
title: "Wireless Internet Driver Issues"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by alanfang on 2009-02-21
I have a Ralink 8701 wireless card on my MSI Wind. I have been struggling to find the correct drivers to install this. If anyone could point me in the right direction it would be greatly appreciated.

---

### Post by cariboo on 2009-02-21
Have a look at this [blog]("http://chris.merrillblogs.com/2009/01/05/msi-wind-mac-wireless-80211bgn-1t2r/") entry.

Jim

---

### Post by alanfang on 2009-02-21
Thanks for the link, now the issue is I can't install the unrar package that is needed to install the wireless card drivers. I have downloaded unrar and do "sudo apt-get install unrar" and it continues to tell me the unrar package is unavailable.

---

### Post by alanfang on 2009-02-21
I managed to solve the rar issue, but I still can't get it to make the driver. Is there a direct download of just the driver somewhere by any chance? Or another way to do this?

The error that seems to be causing the problem is:

cannot write to var/cache/man/cat7/atl1e.7.gz in catman mode atl1e

EDIT: It appears the directions you posted are for wired, not wireless internet. Guess I'll have to take a look at something else.

---

### Post by phndrummer on 2009-02-21
Here is a link to the Ralink linux support page

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
it might not have the right driver.

If your still stuck then google search the brand, model, ubuntu, and 'driver download'

---

### Post by alanfang on 2009-02-21
> **phndrummer said:**
> Here is a link to the Ralink linux support page

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
it might not have the right driver.

If your still stuck then google search the brand, model, ubuntu, and 'driver download'

That's what I have been working for trying to make it a driver. I have searched as you have suggested but that's the only thing I can come up with. Frustrating...

---

### Post by alanfang on 2009-02-21
Yet another update, I *think* I have the wireless driver installed, but I am still getting no internet. What other setup do I need to do besides installing the driver?

---

