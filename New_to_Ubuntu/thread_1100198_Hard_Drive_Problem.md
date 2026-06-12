---
title: "Hard Drive Problem"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by vividia on 2009-03-18
I run Intrepid and my hard drive does not seem to accurately display the amount of memory that is currently used.  I download a lot and then slap the files onto DVDs and delete theme (and empty the trash can) but eventually, the hard drive tells the wrong amount.  I get to the point where the hard drive is full.  When this happened the first time, I rebooted since thats the first thing I do when anything from my cell phone to my computer messes up.  It goes back to a much larger number of free space but then the situation slowly works back to critical mass of sorts.

Not a problem per se.  It's similar to driving a car with a gas gauge that doesn't work.  But after a couple of months of this, I have the time to fix this.  Anybody know?

---

### Post by HermanAB on 2009-03-19
It is a known bug in the ext3 file system.  An upgrade should fix it.

Cheers,

Herman

---

### Post by OllieGab on 2009-03-22
> **HermanAB said:**
> It is a known bug in the ext3 file system.  An upgrade should fix it.

A newbie follow on question...you couldn't please tell me how to do that upgrade, could you? I have a similar problem with my Ubuntu (8.10).

Cheers Ollie

---

### Post by James_Lochhead on 2009-03-22
System > Administration > Update Manager

If it isn't there then it is probably coming in a later release.

He could also mean upgrade to ext4.

Jaunty is coming in just over a month now, when it is here you will be able to use the ext4 filesystem.

---

### Post by hobo on 2009-03-22
> **HermanAB said:**
> It is a known bug in the ext3 file system.  An upgrade should fix it.

Cheers,

Herman

Herman, Would you please be more specific...ie bug reports, etc.

---

### Post by vividia on 2009-03-24
Sorry to not follow my own thread.  It was the last bit of Spring Break.

So I'd need to upgrade how?  I don't think I get a choice when I clean install Intrepid to do either ext3 or ext4.  Is this bug in intrepid or ext3?

---

