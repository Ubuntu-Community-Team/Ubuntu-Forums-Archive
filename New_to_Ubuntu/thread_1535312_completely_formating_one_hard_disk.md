---
title: "completely formating one hard disk"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by 13k on 2010-07-20
Hello,  okay, i'm really cheap as hell... i don't want to buy more cds, floppy disks, more hard disks just to reformat ONE hard disk...  I wish to format my one hard disk for my friend, and erasing all the data of it.  The problem is, without any tools, how can I format my computer completely?  If it's not possible, i guess i'll use a cd....

---

### Post by new__buntu on 2010-07-20
Are you formatting the hard disk to prepare it for a new OS, or to destroy the data on it?

---

### Post by 13k on 2010-07-20
> **new__buntu said:**
> Are you formatting the hard disk to prepare it for a new OS, or to destroy the data on it?

 both actually

---

### Post by new__buntu on 2010-07-20
Whatever you're booting to when you install the new OS (disc, USB, etc) should have the capacity to reformat the drive after you boot to it. The following site has instructions for downloading and installing Ubuntu via flash drive or cd. If you have a flash drive with more than 2 gigs of free space you can avoid using the CD's or DVD's you so dread, otherwise, sorry I'm not sure how to help you: [URL="http://www.ubuntu.com/desktop/get-ubuntu/download"]http://www.ubuntu.com/desktop/get-ubuntu/download
[/URL]

---

### Post by 13k on 2010-07-20
> **new__buntu said:**
> Whatever you're booting to when you install the new OS (disc, USB, etc) should have the capacity to reformat the drive after you boot to it.

 ummmm... yes... i'm somewhat aware of that... what i am asking is... what can i do in ubuntu/windows to completely format my computer or through cd...  too delete ALL the information... from the hard disk, and the junk that still lingers around inside it... and i still have 1 hard disk btw...

---

### Post by Golem XIV on 2010-07-20
Darik's  Boot 'n' Nuke:
[http://www.dban.org/](http://www.dban.org/)

Caution: Use with extreme care.  Any data wiped with dban is unrecoverable.

---

### Post by 13k on 2010-07-20
> **Golem XIV said:**
> Darik's  Boot 'n' Nuke:
[http://www.dban.org/](http://www.dban.org/)

Caution: Use with extreme care.  Any data wiped with dban is unrecoverable.

 i reformated my computer before, will this delete EVERYTHING? as in make almost everything unrecoverable?  i know nothing is 100% =( lolz :P

---

### Post by lolzwut on 2010-07-20
formatting is not a fun thing to do

---

### Post by 13k on 2010-07-20
> **lolzwut said:**
> formatting is not a fun thing to do

 yes, it's not a fun thing to do, but how does this answer my question?

---

### Post by lolzwut on 2010-07-20
> **13k said:**
> yes, it's not a fun thing to do, but how does this answer my question?

why would I want to ever answer your question? Are you gonna pay me to do it? No, then learn how to do it yourself. I'll just sit back and watch you ruin your hard drive :popcorn:

---

### Post by 13k on 2010-07-20
> **lolzwut said:**
> why would I want to ever answer your question? Are you gonna pay me to do it? No, then learn how to do it yourself. I'll just sit back and watch you ruin your hard drive :popcorn:

 lolz, guess so, nice troll... :P true i'm not gonna pay you, but even if i did i'm just guessing you don't even know how to. how would you know i'd ruin my hard drive? btw, i already tried, but got too confusing so sue me? :P have fun trolling..

---

### Post by 101011010010 on 2010-07-20
Hello,
  "Darik's Boot and Nuke ("DBAN") is a self-contained boot disk that  securely wipes the hard disks of most computers. DBAN will automatically  and completely delete the contents of any hard disk that it can detect,  which makes it an appropriate utility for bulk or emergency data  destruction."
[http://www.dban.org/](http://www.dban.org/)
I hope this helps.

---

### Post by 13k on 2010-07-20
> **101011010010 said:**
> Hello,
  &quot;Darik's Boot and Nuke (&quot;DBAN&quot;) is a self-contained boot disk that  securely wipes the hard disks of most computers. DBAN will automatically  and completely delete the contents of any hard disk that it can detect,  which makes it an appropriate utility for bulk or emergency data  destruction.&quot;
[http://www.dban.org/](http://www.dban.org/)
I hope this helps.

 ty, more helpful than lolzwut the troll

---

### Post by Golem XIV on 2010-07-21
> **13k said:**
> i reformated my computer before, will this delete EVERYTHING? as in make almost everything unrecoverable?  i know nothing is 100% =( lolz :P

As I said, any data on a disk erased by Darik's Boot 'n' Nuke is not recoverable.

You could also boot from any Linux live CD, open a terminal and type

```
dd if=/dev/urandom of=/dev/sda
```

You will probably have to do it as root (su or sudo).  This will write random garbage on the entire disk, effectively destroying all data on it.  It is practically the same thing that dban does.

Again, be VERY careful about what you're doing.  After one of the above operations there is no going back.

---

### Post by 13k on 2010-07-22
> **Golem XIV said:**
> As I said, any data on a disk erased by Darik's Boot 'n' Nuke is not recoverable.

You could also boot from any Linux live CD, open a terminal and type

```
dd if=/dev/urandom of=/dev/sda
```You will probably have to do it as root (su or sudo).  This will write random garbage on the entire disk, effectively destroying all data on it.  It is practically the same thing that dban does.

Again, be VERY careful about what you're doing.  After one of the above operations there is no going back.

ummm i kinda don't get the command because, after i wrote that command, the line after became blank in the terminal, do i have to wait for something or wait until it i see my root name?

---

### Post by Golem XIV on 2010-07-23
It takes a LONG time.  Long as in overnight, or more if it is a big disk.

You are writing a full disk's worth of random data, after all.

Edit: [Here]("http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux") are some more details and alternatives.

---

