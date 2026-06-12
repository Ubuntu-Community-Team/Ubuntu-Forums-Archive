---
title: "/dev/ramzswap0 and me"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Didius Falco on 2009-05-16
Greetings,

I check ```
fdisk -l
``` and ```
blkid
``` at least daily. Today I saw something that had never turned up before:

```
 /dev/sda1: UUID="F454DABF54DA83B0" LABEL="WinXP" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="17dc755b-447b-4d6e-ba41-b60ef443d2ae" 
/dev/sda6: LABEL="810Root" UUID="fa76beb9-efb4-4e82-ae63-68b10d9ddaa9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="810Home" UUID="425a90ab-ea30-4a3a-a62e-d171e9844783" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="01C95D7514150B10" LABEL="FileStorage" TYPE="ntfs" 
/dev/sda9: UUID="506DAEE2277A4CAF" LABEL="Backups" TYPE="ntfs" 
/dev/sda10: UUID="b6db7389-4840-4362-9685-fa57a431d8b5" SEC_TYPE="ext2" TYPE="ext3" LABEL="904LiveCD" 
/dev/sda11: UUID="e02ddaef-9065-4851-a66f-b417af080bc6" TYPE="ext3" LABEL="904Default" 
/dev/sda12: LABEL="Data" UUID="1e6ae425-84ca-4fb7-949b-6f38e2b24c67" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: UUID="b99e7427-253b-4f2c-b72f-b494e8955ddb" TYPE="ext4" LABEL="Jaunty64" 
/dev/sda14: UUID="e47525af-4710-4faa-bc80-fbad1ec6d109" SEC_TYPE="ext2" TYPE="ext3" LABEL="Karmic" 
/dev/ramzswap0: TYPE="swap" 
```I immediately hit Google, and was able to find out what it is and why it is sometimes used - for low ram situations on older machines and laptops with less than 256 megs of Ram, particularly for installation.

What I can't figure out is why it has suddenly appeared on my PC, which has 4 Gigabytes of Ram. More importantly, how do I turn it off?

I am running the Alpha of Karmic, so that could have something to do with why it suddenly appeared...but I still don't need and/or want it.

All advice and expertise gladly accepted.

Regards,

Didius

On Edit: Thank you for what I consider high praise, Sir Jasper. It isn't causing any harm, other than a burning curiosity, and I generally have that all the time anyway, so I'm content to let it drift down the pages so as not to block messages from those that really need help.

Regards,

Didius

---

### Post by Sir Jasper on 2009-05-16
Hi,

Because you so frequently help others I'm bumping your question.

This is way way above my pay grade so I can't help directly.

My regards

Addendum:
Sir Didius, I'm sure many of us are well pleased to know your query is resolved.

---

### Post by mprince on 2009-05-16
Not absolutely sure, but I think this thread has what you are looking for:

see post#4

[http://ubuntuforums.org/showthread.php?p=7268741](http://ubuntuforums.org/showthread.php?p=7268741)

---

### Post by KCormier on 2009-05-16
[http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

that seems to be the source of it :).  I read a few other articles and thought the idea was completely stupid.  That page explains the benefits of it much better though!  should explain it all for you :)

-Kevin

---

### Post by Didius Falco on 2009-05-16
> **mprince said:**
> Not absolutely sure, but I think this thread has what you are looking for:

see post#4

[http://ubuntuforums.org/showthread.php?p=7268741](http://ubuntuforums.org/showthread.php?p=7268741)

That did the trick! [COLOR=Red]Thank you[/COLOR] for the kind assistance, and a new piece of info for my linux library.


Regards,

Didius

---

### Post by Didius Falco on 2009-05-16
> **KCormier said:**
> [http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

that seems to be the source of it :).  I read a few other articles and thought the idea was completely stupid.  That page explains the benefits of it much better though!  should explain it all for you :)

-Kevin

I pretty much found out everything about it except how to turn it off, but thanks to mprince I know how to do that now too! ](*,)

Regards,

Didius

---

