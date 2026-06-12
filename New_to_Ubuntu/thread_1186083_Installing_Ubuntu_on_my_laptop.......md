---
title: "Installing Ubuntu on my laptop......"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Christopher on 2009-06-13
I have Acer Aspire AS7720-6536  [http://www.newegg.com/Product/Product.aspx?Item=N82E16834115487](http://www.newegg.com/Product/Product.aspx?Item=N82E16834115487)   I want to dual-boot Vista & Ubuntu and was wondering if anyone has this laptop and has installed Ubuntu on it or IF Ubuntu will or should install on this laptop with no problems.  Thank you in advance.

Should i go with 64bit or 32bit ?

---

### Post by Christopher on 2009-06-13
Anyone ?   :D

---

### Post by QIII on 2009-06-13
The 64/32 bit question comes down to what you want.  If you have a 64 bit system (which it appears you do) the 32 bit distro will work on it just fine.  (That can't be said of a 64 bit OS on a 32 bit machine, of course.)

But if you really want the 64 bit system, go with it.

The only thing I see that might be of concern is your video card.  I'm not an expert with nVidia cards, but I see a lot of discussion about them.

I'd recommend doing a search through the forum.  I've seen people post quite a bit of info regarding nVidia card support.  If yours is a relatively new machine, you will probably be OK.

---

### Post by Christopher on 2009-06-13
> **QIII said:**
> The 64/32 bit question comes down to what you want.  If you have a 64 bit system (which it appears you do) the 32 bit distro will work on it just fine.  (That can't be said of a 64 bit OS on a 32 bit machine, of course.)

But if you really want the 64 bit system, go with it.

The only thing I see that might be of concern is your video card.  I'm not an expert with nVidia cards, but I see a lot of discussion about them.

I'd recommend doing a search through the forum.  I've seen people post quite a bit of info regarding nVidia card support.  If yours is a relatively new machine, you will probably be OK.

Thank you for replying, how about my wireless adapter any issues with those on laptops with unbuntu?

---

### Post by QIII on 2009-06-13
I have seen several posts on the subject (Jeez! I'm sorry I keep giving you vague answers.  Not very helpful!)

I know I just read through a post a few days ago where someone was venting and frothing about the subject.

You'll probably get a lot of hits, but do a search on "wireless".

For that particular guy, there were a lot of responses to the effect that he should just buy a new device.  Eventually someone pointed him to a less costly solution.

---

### Post by waspbr on 2009-06-13
the best thing to do here would be to boot the computer with a live CD, preferebly jaunty since it has got more updated hardware support. You can check how things work, if wireless works and whatnot. 

provided it doesn't you can post the output of

```
lspci
``` 

so we can have a more insightful look at your hardware.

good hunting

---

### Post by ugm6hr on 2009-06-13
> **waspbr said:**
> the best thing to do here would be to boot the computer with a live CD, preferebly jaunty since it has got more updated hardware support. 

This is easy, and will give you an immediate indication of the potential problems.

---

### Post by Christopher on 2009-06-13
Awsome, thank you everyone for all of your help.:D

---

### Post by Christopher on 2009-06-13
Ok im running on the 64bit jaunty 9.04 live cd & i have internet access and everything seems to be working awsome on my laptop. the question i have is i put my mouse arrow over the network signal and it reads active name of the network then says 72%, whats the 72% mean, sign al strength? on vista its 95% at the same location. Thank you in advance.

Can I use the vista admin tools to re-size my hard drive then defrag and install Jaunty 9.04 onto that partition?

---

### Post by Christopher on 2009-06-13
> **Christopher said:**
> Ok im running on the 64bit jaunty 9.04 live cd & i have internet access and everything seems to be working awsome on my laptop. the question i have is i put my mouse arrow over the network signal and it reads active name of the network then says 72%, whats the 72% mean, sign al strength? on vista its 95% at the same location. Thank you in advance.

Can I use the vista admin tools to re-size my hard drive then defrag and install Jaunty 9.04 onto that partition?


Anyone? :D

---

### Post by SoftwareExplorer on 2009-06-13
The percentage is indeed the strength of the signal, but if it works, it's probably just fine. 

As far as resizing Vista, just defragment from Vista before installing Ubuntu and the Ubuntu installer can shrink the Vista partition.

---

### Post by ugm6hr on 2009-06-13
> **Christopher said:**
> Ok im running on the 64bit jaunty 9.04 live cd & i have internet access and everything seems to be working awsome on my laptop. the question i have is i put my mouse arrow over the network signal and it reads active name of the network then says 72%, whats the 72% mean, sign al strength? on vista its 95% at the same location. Thank you in advance.

Can I use the vista admin tools to re-size my hard drive then defrag and install Jaunty 9.04 onto that partition?

Yes.  The 72% is wifi signal strength.  Don't worry that it is different than in Vista. The numbers are not directly comparable, as I understand it; I think signal strength is measured in a different way.

Yes. Use Vista's built-in disk resizer to defrag and then resize (leaving blank space for Ubuntu).  It is then easy enough to use the largest free space guided option in the Ubuntu installer.

Also - don't repost within 24 hours of asking a question until someone else responds - it's bad forum etiquette.

---

### Post by Christopher on 2009-06-13
> **ugm6hr said:**
> Also - don't repost within 24 hours of asking a question until someone else responds - it's bad forum etiquette.

Ok, sorry for that.

Thank you everyone for all of your help.

---

