---
title: "Is this true (partitions)?"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Dreakon on 2010-01-14
Is it true that running Ubuntu on a seperate partition (for dual booting, lets say) will negatively effect it's performance?  Would I see an improvement in how it runs if I got rid of all partitions and just sat Ubuntu on the full 250gb hard drive?

---

### Post by lindsay7 on 2010-01-15
I have computers set up each way and can not tell any difference.  So, just do what you want that makes you happy.

---

### Post by Sef on 2010-01-15
Never heard of that.  If anything I would think it would run faster since Ubuntu is on a smaller partition.

---

### Post by baddog144 on 2010-01-15
I can't see why it would make any appreciable difference.

---

### Post by Dreakon on 2010-01-15
> **Sef said:**
> Never heard of that.  If anything I would think it would run faster since Ubuntu is on a smaller partition.
Lol, someone said it to me at some point.  It sort of makes sense.  If it has less breathing room, it's bound to struggle a little more.  Whereas sitting on a larger partition, any extra space the O/S might need for just about anything is readily available.

That's beside the point though, sounds like it doesn't make much of a difference.

Just out of curiosity, would putting Ubuntu on a smaller partition and keeping the rest of my hard drive for personal files and music and stuff work out better if I want to upgrade Ubuntu to future versions?

Also, if I want to put Ubuntu on that smaller partition, what size would you recommend I make it?  Would 20gb be a good idea?  For Ubuntu, Windows XP (for VirtualBox), any software I might need, maybe some moderately sized games and the swap?

---

### Post by egalvan on 2010-01-15
true or not, doesn't really matter... :)

any speed differences would be basically un-measurable by NORMAL computer USERS.

Esoteric benchmarks MAY be able to discern differences.

Now if your computer usuage is is running esoteric benchmarks,
 then you'll find that any OS runs "faster" if the I/O is split onto different spindles. :)

---

### Post by running_rabbit07 on 2010-01-15
No, I have had it single booted,dual booted, triple booted, and very briefly quadruple booted and it seemed as fast every which way I had it. The quad boot was XP, Fedora 11, Debian Lenny, and Ubuntu Jaunty. D-Fed found their way out pretty quickly.

---

### Post by Sef on 2010-01-15
> Also, if I want to put Ubuntu on that smaller partition, what size would you recommend I make it?  Would 20gb be a good idea? 

8 -10 gb is more than enough for Ubuntu.

---

### Post by Chilli Bob on 2010-01-15
There can be a performance loss if you are constantly working between partitions.  For example if all your photos and music are in your windows partition, and you are accessing them constantly from your ubuntu partition, there may be a small loss of performance.  If you are only working in one partition, the presence of another partition won't affect anything.

There is also a small loss of performance where your /home partition is separate from the rest of Ubuntu, but it is tiny, and well worth keeping separate IMHO.

---

### Post by Dreakon on 2010-01-15
> **Sef said:**
> 8 -10 gb is more than enough for Ubuntu.
Even if I intend to include an installation of Windows XP for virtual purposes on the partition?  Or should I take that into account as well?

> **Chilli Bob said:**
> There is also a small loss of performance where your /home partition is separate from the rest of Ubuntu, but it is tiny, and well worth keeping separate IMHO.
What is the /home partition and why would it be seperate from the rest of Ubuntu?  From I could tell it was included on the same partition as it... unless I'm thinking of something else.

---

### Post by running_rabbit07 on 2010-01-15
No. If you plan on doing VBox installs, you will need about 20 Gigs for Ubuntu.

---

### Post by Dreakon on 2010-01-15
> **running_rabbit07 said:**
> No. If you plan on doing VBox installs, you will need about 20 Gigs for Ubuntu.
Is 20gb a safe amount to put it at?  Would you recommend it or should I maybe bump it up to 25gb for some buffer room?

---

### Post by running_rabbit07 on 2010-01-15
Anywhere between 20 and 25 will be great. If you start adding stuff like Ubuntu Studio or Edubuntu, you will run out of space. VBox usually sets the virtual hard drive for the OS at 8 gigs. Windows XP will quickly grow to about 4.5 to 5 gigs after doing all of the updates and adding AV and such. I had an XP Pro VBox for a few months to do school projects and I think it finally grew to 7 gigs, but that is with me saving lots of large data files for the school program I was running.

---

### Post by Dreakon on 2010-01-15
Alrighty, sounds like 27gb (and extra 2gb for swap) is a solid number to go with, and leaves me 223gb for everything else I have lol.

Quick question, if I create the partition for Ubuntu before I install it, then simply do a fresh installation of Ubuntu onto that new 27gb partition... will it load Ubuntu when the installation is over, or Windows from the larger partition?  Or will it use the GRUB menu, whether I choose the "side-by-side" option or not during installation?  I would rather it just load Ubuntu automatically without the grub menu, then just let me deal with the Windows partition myself in Ubuntu.  I'm hoping it will just load the last O/S I installed onto the hard drive lol.

Also, will I need to create the swap partition before the installation or does Ubuntu set aside space for the swap on its own?  If I create it beforehand, will it simply ask what partition I want to use for swap during installation?

---

