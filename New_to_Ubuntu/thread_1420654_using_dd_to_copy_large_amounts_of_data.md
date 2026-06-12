---
title: "using dd to copy large amounts of data"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by shortridge11 on 2010-03-03
I have several harddrives full of information.  I'm moving the information from 1 TB drives to 1.5 TB drives for future storage needs.  Would it be slower or stupid for some reason to just use dd to clone the stuff from a 1 TB to a 1.5 TB drive?

---

### Post by psusi on 2010-03-03
Yes.  Not only would it waste time copying all of the free space, but it would not resize the filesystem to use the larger disk.

---

### Post by Objekt on 2010-03-03
Been there done that.  Not knowing any better, I once used dd to take an image of a 40 GB hard drive and store it on a 1 TB external HDD.

Or at least that's what I thought I was doing.  I ended up with a 1 TB drive that thought it was a 40 GB drive, having the contents of the original 40 GB drive.  I had to reformat the 1 TB drive to get it back to full capacity.

Fortunately, I was only testing, so no data were harmed in the experiment.  It did make me reluctant to mess with dd ever again, however.

Just doing a direct copy, using Nautilus or whatever, is the best way to do what you want.

---

### Post by handy on 2010-03-03
Have a look at Clonezilla, it is easy to use & from my experience far more reliable than dd.

If it suits your purposes you are on a winner.

---

### Post by iponeverything on 2010-03-03
> **handy said:**
> Have a look at Clonezilla, it is easy to use & from my experience far more reliable than dd.

If it suits your purposes you are on a winner.

Goodness. Please elaborate on the "far more reliable than dd" statement. dd is not a complex piece of code, I am curious about how in the world it could be unreliable.

I am not arguing that dd is better than Clonezilla, just that it does not get more more basic than a bit by bit copy.

---

### Post by Objekt on 2010-03-03
I don't know about "reliable," but to me, Clonezilla is certainly easier to use - and get the desired result! - than dd.  It also is a bit less overhead than a normal Linux Live CD, making it faster to boot and able to run on pretty much any hardware, however old.

I'm pretty sure Clonezilla uses dd in its inner workings, it's just hidden from the user.   So it's kind of silly to say Clonezilla is better than dd.  It's more accurate to say that Clonezilla makes dd more accessible, and is less likely to cause an "oopsie."

---

### Post by handy on 2010-03-03
> **iponeverything said:**
> Goodness. Please elaborate on the "far more reliable than dd" statement. dd is not a complex piece of code, I am curious about how in the world it could be unreliable.

I am not arguing that dd is better than Clonezilla, just that it does not get more more basic than a bit by bit copy.

I used dd to clone a 1TB drive to a 1.5TB drive.  There were multiple partitions including the following file systems: fat32, HFS+, Ext3, JFS.

After a looong time, dd gave me a result where I could boot OS X, but I could not, no matter what trick I tried, & I tried every one I could find (some hours wasted there) re. Grub & whatever else; I could not get Arch to boot, even though it was all there on the partitions.

So then I did the same thing using Clonezilla; it was easier, it was quicker & it just worked.

This is the experience on which I base my statements.

I will never directly use dd again. Though Clonezilla does & did use dd for a part of the operation that it performed for me.

Clonezilla has shown itself to have a great deal more intelligence than dd, as it uses dd as a tool when required, then switches to another tool, & so on.  

Whatever combination of tools are appropriate to the file systems in front of it, are what Clonezilla uses.

---

### Post by HermanAB on 2010-03-03
Well, it is not like you are going to sit there and watch it copy all the bits are you?  So how long data definition takes to copy the whole drive doesn't really matter.  However, I would use rsync, because your drives probably have lots of empty space that don't need copying and rsync uses cryptographic checksums to ensure that the data is copied correctly.

---

### Post by iponeverything on 2010-03-03
> **Objekt said:**
> I don't know about "reliable," but to me, Clonezilla is certainly easier to use - and get the desired result! - than dd.  It also is a bit less overhead than a normal Linux Live CD, making it faster to boot and able to run on pretty much any hardware, however old.

I'm pretty sure Clonezilla uses dd in its inner workings, it's just hidden from the user.   So it's kind of silly to say Clonezilla is better than dd.  It's more accurate to say that Clonezilla makes dd more accessible, and is less likely to cause an "oopsie."

I agree, the trail is littered with stories of dd command typo's causing martial discord.

---

### Post by handy on 2010-03-03
As stated previously, dd is just one of a variety of tools that Clonezilla uses.  

Clonezilla chooses which tool depending on the file system & probably also on whether you are cloning or creating images.

Also, when I used dd I made VERY sure that the command I entered was correct.  I read a very good how-to, & also talked on a forum, & quadruple checked for typos. ;)

---

### Post by dpacmittal on 2010-03-03
Just use rsync. Its good, IMO.
I used it when I shifted from 160GB to 500GB. However, it won't copy boot-records. So, that'd be a problem. You could just re-install grub for that.

---

### Post by psusi on 2010-03-03
rsync is good if you need to frequently update the copy, but just doing it one time cp works just as well.

---

