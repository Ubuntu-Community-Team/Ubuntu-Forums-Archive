---
title: "dual boot and grub 2"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by neilscrim on 2011-01-24
It's time to fess up, I'm a newbie to linux, I really want to love linux but it's doing its best to cheese me off. 

A bit of background for you before I get to the questions.

The first time I installed ubuntu using wubi (on a dual boot PC with XP and Vista) i ran the wubi installation from Vista and lost the mbr, it was completely unrecoverable (nothing would repair it, not windows recovery or Live CD).

Fast forward a few months and it was time to try ubuntu again.

Being wise to the previous event, I decided to do things different on my laptop which is also a dual boot but has 3 partitions (C is Vista, D is XP and E is for data). I ran wubi from XP and put ubuntu on the E drive.

So I ended up with a laptop with 3 OSs (XP, Vista and 10.04) and all was well... kind of.

On initial boot up I would get the Vista boot menu which lists Vista, XP and Ubuntu. However, you can't run ubuntu from here, it just doesn't work. If you chose XP from this first boot menu you then get another boot menu (which obviously belongs to XP) which lists options of XP or Ubuntu and both worked fine.

OK so far so good...then came along grub 2...

I did all the updates for 10.04 which included grub 2 and once again the mbr got screwed.

To cut a long story short I managed to recover the laptop to give me Vista and XP on a boot menu. I then installed 10.04 (via wubi in xp) on the E drive again, did the updates and this time unchecked the grub update. All is well and I now have 3 OSs again.

So my questions are:
do I need grub 2?
is there an alternative to grub 2?

I would ask a 3rd question, what the **** is going on with grub2? However it seems I'm not alone with this problem, hopefully someone is working to fix it.

---

### Post by Rubi1200 on 2011-01-24
Hi and welcome to to the forums :)

There are known issues with GRUB updates breaking Wubi installs.

For an overview of the issues and solutions, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you installed Wubi recently and have not updated anything yet, follow the instructions in the main post just after the Permanent Fix on how to lock the grub-pc and grub-common packages so this won't happen in future.

---

### Post by wilee-nilee on 2011-01-24
To be honest since you have XP and Vista their boot is tied together, you might want to consider doing a real partitioned dual boot or triple here. Ubuntu in this format would be stable and grub would show a windows stanza that would take you to the MS boot from menu.

---

### Post by neilscrim on 2011-01-25
Thanks for info guys.

A triple boot with ubuntu on it's own partition isn't a go-er for various reasons. :(

I think I'll plod along with my existing grub until either a) I need to upgrade or b) I pluck up enough courage to update grub to v2 and deal with the consequences. :)

Neil

---

