---
title: "Swapping HDD"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by nitoplayer on 2010-07-28
So I got a new machine and was wondering if I can just throw my old HDD in it and I would start off right where I left of(plus some extra time DL'ing new drivers and whatnot).

Or do I have to install ubuntu on the new machine, get all my crap off the old HDD, then start off again?

Any thoughts?

---

### Post by Goolie on 2010-07-28
I'm 85% sure that won't be the best method.  But I'm 15% sure I'm wrong.

I would just throw the HDD in and format it and install Ubuntu fresh.  You could always save files and stuff by throwing it on a DVD / external HDD.

---

### Post by nwadams on 2010-07-28
theoretically it should boot or attempt to boot depending on what kind of hardware you had previously. Give it a shot, if it works, it works, if it doesn't, it doesn't. I would still recommend doing a backup and re-install if you have any issues or if your hardware is very different

---

### Post by nitoplayer on 2010-07-28
It was from an Lenovo T61 and going to a T510 so I would think it will work for the most part. 

Since it is a Windows machine to begin with I was wary on its ability to find the OS, but then again I was fairly sure that it being Windows didn't matter.

---

### Post by jtarin on 2010-07-28
You must make sure you have it configured in the bios as to boot order. If they are both SATA drives no need to configure a Master/Slave jumper setting. Master and Slave only matter on EIDE systems, or ATA,whatever label you want these days. Window likes to be first in boot order, so this might make a difference in your Grub configs, depending on what your present disk has installed.

---

### Post by 23dornot23d on 2010-07-28
If you have it as a [second drive]("http://www.geeks.com/products_sc.asp?cat=405") .... you can use it to get to your data.

[B]How big is this drive and how much data do you have on it ?
[/B]
Are you wanting to boot from it .... often they can boot , [B]but its not a good thing to do
especially when all your hardware is different[/B].

They can get stuck when they come to things like setting the graphics or looking for networks etc  ...... a lot depends on what you had before and how similar it is to your new setup.

[B]IMHO ..... just use it for the DATA ...... or if you have enough space on it resize it and use the free space for a new LINUX OS ......
 [/B]
Gradually move the DATA to the new drive and then at some point format the old one or you could keep it as a backup.

---

### Post by Michael Dooley on 2010-07-28
> So I got a new machine and was wondering if I can just throw my old HDD in it and I would start off right where I left off (plus some extra time DL'ing new drivers and whatnot).

Or do I have to install ubuntu on the new machine, get all my crap off the old HDD, then start off again?

Any thoughts?

Should work flawlessly. I swap hard drives between vastly different computers way too often and must say, Ubuntu just works.

---

