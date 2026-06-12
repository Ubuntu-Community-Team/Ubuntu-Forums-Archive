---
title: "method to have &gt;4 pri. partition"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-07-25
I want to install more OS but the limitaion of 4 primary partition is creating obstacle. Is there is any method to make more primary partition?

Thank You

---

### Post by Wataru8675 on 2009-07-25
Can't you make partitions in external hard drives?  Or can you not run OS'es off them?

---

### Post by ptn107 on 2009-07-25
You can have an extended partition with as many logical partitions as OS's you need.

You can go from four primary (p=primary, e=extended, l=logical):
sda1 (p)
sda2 (p)
sda3 (p)
sda4 (p)

To something like:
sda1 (p)
sda2 (p)
sda3 (p)
sda4 (e)
 sda5(l)
 sda6(l)
 sda7(l)
 ... and so on.

---

### Post by eshant_engineer on 2009-07-25
somebody had told me that windows OS does install on primary partition. It can be install on logical partition but Grub would not be able to point inside extended partition and also i had tried by installing xp in extended partition. But Grub was not able to branch me to windows xp which was in first logical partition(i had updated the menu.lst).

---

### Post by jerome1232 on 2009-07-25
What operating systems are you booting, yes Windows XP does require being on a primary partition, Linux however can be on Logical partitions.

Unfortunately this limitation of 4 primary partitions can't be bypassed.

---

### Post by oldfred on 2009-07-25
Here is some info on multibooting:
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

You can install 3 versions of Windows in primary partitions and many versions of Linux in extended partitions per hard drive.

---

### Post by eshant_engineer on 2009-07-25
> **oldfred said:**
> Here is some info on multibooting:
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

You can install 3 versions of Windows in primary partitions and many versions of Linux in extended partitions per hard drive.

So in such configuration, will Grub work?

---

### Post by mikechant on 2009-07-27
> So in such configuration, will Grub work?

If it's set up correctly, then yes!
Most of the time, if you install Ubuntu (or another distro) after installing one or more windows versions, it will detect and create grub menu entries for all the existing windows and linux installs. Sometimes you need to do a bit of manual tweaking.

---

### Post by egalvan on 2009-07-27
This has long been a favorite read of mine...
it even gets an update or two...


*How to install and boot **145 operating systems** in a PC*

[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)


A quote from the author

*[COLOR="Red"] I have managed to run a Ubuntu from sda130![/COLOR] *

---

### Post by mikechant on 2009-07-28
> I have managed to run a Ubuntu from sda130!

Interesting. I was still thinking the safe limit was 15 partitions per disc for Linux (as it used to be). However, 'sda130' is still dodgy (i.e. not supported by various utiltiies) acording to this interesting article (referenced by the '145 operating systems' article):
[http://www.justlinux.com/forum/showthread.php?t=152404](http://www.justlinux.com/forum/showthread.php?t=152404)
Looks like 60ish is the safe amount now.

---

### Post by egalvan on 2009-07-30
> **mikechant said:**
> the **safe limit** was 15 partitions per disc

 'sda130' is still **dodgy** (i.e. not supported by various utiltiies)

Looks like 60ish is the safe amount now.

"safe" ? 
"dodgy"?

we are talking about installing 145 different OS's on one machine. :P

I respectfully submit that stability is not one of the overriding decisions in this quest :)

It's all about pushing the limit.

True, it's nice to have a stable computer,
but if you have over one hundred systems to choose on boot,
how much time can each one run?

It's like asking a drag racer to be "stable"...
he wants to go fast!

Or a weight lifter to "safe"
he wants to lift weight!

It's also about having fun,
and being able to boast

"Mine's longer that yours!"

My boot menu, I mean!

---

### Post by presence1960 on 2009-07-30
> **egalvan said:**
> "safe" ? 
"dodgy"?

we are talking about installing 145 different OS's on one machine. :P

I respectfully submit that stability is not one of the overriding decisions in this quest :)

It's all about pushing the limit.

True, it's nice to have a stable computer,
but if you have over one hundred systems to choose on boot,
how much time can each one run?

It's like asking a drag racer to be "stable"...
he wants to go fast!

Or a weight lifter to "safe"
he wants to lift weight!

It's also about having fun,
and being able to boast

"Mine's longer that yours!"

My boot menu, I mean!

True, some of my biggest lessons (not with only computers) have come from trying something that  resulted in breakage/damage. I could have whined about it but instead looked at it in a different way. I looked at it as an opportunity to learn. The best way to learn is to try things, mess it up and then with or without help from others fix it. Usually the fix will teach you what the problem was and why the fix works.

---

### Post by egalvan on 2009-07-31
And I should further add that I only experiment with my non-work computers.

I DO NOT recommend trying to install 145 operating systems on your main machine....
unless your job involves such craziness... :)

The fun of Linux is that it runs on such a wide variety of older equipment,
equipment that is sometimes tossed out as "obsolete" by the MS-Win crowd.
I was given (free, gratis, take it away) an HP machine, because it "only" had
an AMD Sempron running at "only" 1.6GHz, and "only" 512MB RAM...
 it won't run Vista, Great Zot! Out, Out, Damn Machine!

Now it sports an AMD Athlon 64 @ 1.9GHz, 4GB RAM, and an ever-changing line-up of Linux Distros...
last I checked, it was booting WinXP, Hardy, Jaunty and Puppy.

Have Fun!

---

### Post by mikechant on 2009-07-31
I guess my main point (which I didn't make clear) was that you might have a legitimate reason to want more than 16 partitions even on a non-experimental box, and this is now possible and safe with current Linux kernels (and wasn't before).

---

