---
title: "How come Freespire Can Get It Right (Broadcom BCM4318)"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by fred22 on 2006-09-28
If you read these forums then you may know that the above card and its relatives is the source of much misery for Ubuntu users. Myself included.
I tried running the live cd for Freespire tonight and guess what? I HATE the look of the thing, hate the mixing of free and non-free, but it picks the card up and whats more allows me to connect straight away.

Its embarassingly good.

How can they manage it and we can't?

I would advise anyone with BCM4318 trouble to try a Freespire live cd just to confirm my experience. I would also be very interested in any explanation of the obvious difference in the ability of two Linux distros to support the same hardware, as I am new and proud of it.

Thanks,
Fred

---

### Post by H.E. Pennypacker on 2006-09-28
I have this card too, and my experience with it on Ubuntu has been GREAT.  It took a few steps, and I was done.  Never had to use the terminal again to get it working, and changing settings, and all that.  It's really a breeze.  

Again, it was REALLY that easy.  No disconnects and all that.  If something goes wrong, the problem is probably with my cable company (cable broadband).

If something does go wrong, I go to preferences, and reset the connection.  Give it a second, and it works again.  

Done!  

The problem here is that there are too many guides around, and people don't know which one to use.  I don't recall what it is I did, because there were so many guides.

---

### Post by Emge on 2006-09-28
I have a notebook with the BCM4318, ugh...

I thoroughly trashed the OS with bcm43xx-fwcutter or was it -fwcutter combined with network manager? I had to reinstall Dapper. 

I agree that there are too many guides out there. I'm going slowly this time, wondering what approach to use - ndiswrapper? Or try BCM43xx-fwcutter again? Or pay Linextant $20 for their solution?

Or maybe, I should just replace the freaking card?

Cheers

---

### Post by jamiebux on 2006-12-15
I have a question. I got my wireless working, somewhat, using the bcm43xx tarball. The only problem I'm having is that I can't scan for networks. Even in the bcm43xx script install log, it says that my wireless card will not scan. I have used Network Manager and wifi radar, but nothing has worked. I really need help with this on. I have a Pavilion dv5210 laptop and I have upgraded and configured the wireless card in my BIOS. I really don't know what to do next. Any ideas would help please. My wireless card actually worked perfectly in Freespire. Nothing else did though. 8)

---

### Post by jamiebux on 2006-12-15
I want to do more research on the matter. But I wonder if the reason Freespire works 

with that card is because they are paying to using the proper drivers from Broadcom. 

And If some programming can be done to add the driver from Freespire into Ubuntu. 
 
I don't know about anyone else, but I know that my card was picked up by Ubuntu on the first 

install, but it just wouldn't work until I used the bmc43xx tarball.

Just a thought.

---

### Post by tturrisi on 2006-12-15
from Freespire site:
> Freespire is a community-driven, Linux-based operating system that combines the best that free, open source software has to offer (community driven, freely distributed, open source code, etc.), but also provides users the choice of including  **proprietary codecs, drivers and applications** as they see fit.

proprietary (dictionary.com)
5. manufactured and sold only by the owner of the patent, formula, brand name, or trademark associated with the product: proprietary medicine.

---

