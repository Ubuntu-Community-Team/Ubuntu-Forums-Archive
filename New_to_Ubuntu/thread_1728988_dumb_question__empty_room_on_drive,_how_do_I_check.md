---
title: "dumb question:  empty room on drive, how do I check this?! Adjust for more partition?"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by RotorRick on 2011-04-14
I have Ubuntu 10.4LTS, REALLY like it!

However, my poor laptop only has an 100g drive, and being unsure of Ubuntu at install, chose about 50% for the partition. Since then I've been downloading a fair bit...but now I'm very unsure of just how much or little room I have left...

In Windows world, I could just right-click on the harddrive icon, and it would tell me I have this much free space, that much data. But now in Ubuntu, with the partitions, I'm not sure what I'm looking at. If I click on the "file system", it tells me I have 5.4gigs free, and 39 gigs of content...but is that the free space on my Ubuntu side of the hard drive, or is that the Windows side? And when I right-click on "100gig hard drive___" it doesn't tell me anything useful at all.

I'm fairly certain I'm only using 26gigs on the Windows side of the partition, and I'm guessing I'll need 5 or more gigs free space to actually use that, so is there a way for me to easily adjust the partitions, from say 50%/50% to say 65%/35% ? Or is that difficult or set in stone?

Thanks!!

---

### Post by Elfy on 2011-04-14
```
df -h 
```

will tell you the state of the ubuntu drive. If you mount the windows drive before running it, that'll be there as well. Whether it will report a correct value for the win drive I am not sure, but would expect it to be.

---

### Post by seawolf167 on 2011-04-14
+1 for *df*, if you are wondering what is eating up your space, you can also use [I]du

[/I]```
du -h
man du
```

---

### Post by Cpierce on 2011-04-14
I use gparted. It's easy

---

### Post by Elfy on 2011-04-14
Why is gparted easy when df and du are available but gparted has to be installed?

There are times when a cli command pays dividends - not always, but sometimes ;)

---

### Post by -kg- on 2011-04-15
> **forestpiskie said:**
> Why is gparted easy when df and du are available but gparted has to be installed?

There are times when a cli command pays dividends - not always, but sometimes ;)

I don't know...I'm used to partition editors.  I've used them for years and years.  They will show you the drive(s), the total size of the drive(s), how much is used, how much is free, and give you a nice graphical representation.

I'm an old, old computer user.  I can use CLI (and do!) and understand what the read outs represent.  But sometimes I prefer a graphical representation, and I'm sure that's what some newer computer users are used to, as well.

Besides, like you said...Gparted is installable.  I'll use any tool available to me, especially if it makes it easier to comprehend. ;)

BTW, I'm not pooh-poohing the CLI...I encourage it's use, for those willing and desiring to learn it!  Like you said, it pays dividends, sometimes, but ***only*** if you understand what it's telling you.  And ***that's*** something you have to learn!  Until then...use the tools!

---

