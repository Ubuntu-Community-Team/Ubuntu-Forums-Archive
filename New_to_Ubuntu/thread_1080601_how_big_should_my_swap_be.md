---
title: "how big should my swap be?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by nachos99 on 2009-02-25
i have 2.5 GB RAM.  should i make the swap partition 2 GB?  i've read somewhere that anything larger than 1 GB may be a waste.  i don't know if that's true, but i do know that i would like to run XP on virtualBox.  so i was then wondering if that meant i need a larger swap than 2 GB.

any recommendation is appreciated.

thanks,

---

### Post by Therion on 2009-02-25
I've heard you need a 2GB swap if you want to be able to use the "Suspend" option.  I don't know if that's true or not.  I set my swap to 2.5GB anyway though.  

That old rule of thumb about your swap file being 2.5 x total system RAM is way outdated.  

If in doubt, I'd say:  Set your swap to 2GB and get on with life.

---

### Post by ptn107 on 2009-02-25
> **Therion said:**
> I've heard you need a 2GB swap if you want to be able to "Suspend".  I don't know if that's true or not.  I set my swap to 2.5GB anyway though.  That old rule of thumb about your swap file being 2.5 x total system RAM is way outdated.  If in doubt, I'd say:  Set your swap to 2GB and get on with life.

I think you mean hibernate and I don't think you need 2GB, just enough for what is currently stored in ram.

As for the swap partition size 2GB is sensible.  If your relying on swap too heavily, though, that's a sign you need to increase your RAM.

---

### Post by cerealtx on 2009-02-25
what i have generally heard is double your ram i believe

---

### Post by Bölvaður on 2009-02-25
You need about the same size swap as your top RAM usage when you hibernate your laptop.
If this is on the other hand a desktop a very small one will do.. like 500MiB or even way less.

---

### Post by linuxisevolution on 2009-02-25
I have 713mb of swap with 4gb of ram and I don't have any problems in that area. I used to have 9gb swap by mistake :p

---

### Post by anewguy on 2009-02-25
I come from the old school, but I will give my view:

it used to be that swap (or virtual memory or backing store as it is called in various other OS's) needed to be 2 times the size of your physical memory.  However, this is not the case now unless you are running many applications and they are extrememly memory hungry.  With todays Ubuntu, a swap size of 512mb to 1gb should be more than plenty, with one caviet:  if you are using a laptop, and you plan on using hibernate (be forwarned - you should research your particular laptop and hibernation problems on the forum first), you MAY find you need as much as 2 times your physical memory plus some overhead.  This really should be the exception.  I'm not sure on Ubuntu's snapshot methods, but older OS's were more particular on this.  I think the main problem people run into with hibernation is not a swap problem, but other problems associated with hibernation and trying to wake everything up - video and wireless seem to be the 2 biggest ones.  Start with 512mb - if that doesn't work you can always make it bigger (just be sure when you partition your drive to leave some extra space if needed, or place swap on a different drive altogether).

My current system has 2 gig of main memory, and I really don't use much swap at all.  It is a desktop, so I have no need to try to test hibernation.

Dave ;)

---

