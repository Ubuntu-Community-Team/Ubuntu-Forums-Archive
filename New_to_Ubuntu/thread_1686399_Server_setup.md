---
title: "Server setup"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by l222 on 2011-02-12
I would like to setup a home server on my old desktop and I need to purchase a new hardive.  I was wondering what I should take into  consideration in regards to hard drive size. The desktop is a dell dimension 3000,  1g of ram...IDE hard drive.  I see that you can buy an adapter from ide to sata.

Any help/opinions would be appreciated

---

### Post by CharlesA on 2011-02-12
Anything works. I've run Ubuntu off an 8GB drive before. The last time I went hard drive shopping the smallest I could find was a 160GB drive.

How much space you need depends on what you are going to use the machine for.

---

### Post by metalf8801 on 2011-02-12
What are you planing on using your server for?

If your going to keep important data on it I would recommend using a second hard drive as a redundant backup.

---

### Post by jimwill on 2011-02-12
I'm using an old 450 mhz dell latitude with no keyboard, no display, no mouse, 128 meg memory and a 10gig hard drive. Ubuntu 10.04 server runs fine on it. I use webmin or ssh to log on from my desktop to administer it. I did have to put the hard drive into a laptop that had 512 meg of memory to load the software, but it runs fine on 128 meg.
Also loaded up a CMS website, and html websit, and a website generated from gramps (genealogy). Still have over half the hard drive unused.
(not available to public - personal use only)

---

### Post by l222 on 2011-02-13
Thanks for the replies.

I'm going to use the server mainly as a place to store videos and 
photos.  I may setup up a website and some of the other features.

I may just pickup a 500mb IDE hard drive. I have a 1tb external drive for backup

---

### Post by l222 on 2011-02-14
Looks like the SATA hardirves are much cheper.  My computer has IDE. Has anyone used on of the ide to sata adapters?

---

### Post by SeijiSensei on 2011-02-14
I'm not sure what you mean about a converter.  I'd just buy a PCI SATA card like [these](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007607%20600022622&IsNodeId=1&bop=And&Order=PRICE&PageSize=100).  Dell's specs say you have three PCI slots in that box, so just drop a card like this into one of them.  Oh, and you'll need some SATA cables, if they don't come with the drive itself.

I'd also consider buying two identical drives and setting them up as a RAID1 array using mdadm.

---

### Post by CharlesA on 2011-02-14
+1 to Senji.

That would be the easier way to go about it. I've not used those IDE to SATA converters before, so I can't tell you if they are a good idea or not.

---

### Post by sandyd on 2011-02-14
> **l222 said:**
> Thanks for the replies.

I'm going to use the server mainly as a place to store videos and 
photos.  I may setup up a website and some of the other features.

I may just pickup a **500mb **IDE hard drive. I have a 1tb external drive for backup
???

---

