---
title: "Advice for partitions"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by annie227 on 2009-11-15
I've attached a screenshot of my 500GiB HD thus far in 2 partitions.
First I'd like advice on it's current state and 
second I would like to add another partition for mint7 and/or ubuntu studio(to try).
sda1 is XP,sda2 is "storage" plus I have an external HD
Thanks heaps

---

### Post by Jon Monreal on 2009-11-15
What exactly are you looking to do?

---

### Post by annie227 on 2009-11-15
Wow,you're quick Jon.
Well,first,what do you think of how it's "laid out",eg,is the swap the right size etc?That kind of thing and 
then I'm wanting to install another linux but first I would like to know if I have the right amount of space,MiB's allotted to karmic,xp or if I could shrink them down or whatever.
I'm fairly new at this and value opinions of those who know what they're doing!

---

### Post by raymondh on 2009-11-15
you have one (1) primary partition left (from the 4-rule).  That means you can take space from the NTFS media (or your windows) partition to create that remaining primary and make it for mint.

I don't know if a default mint install will put a swap space/partition.  If so, you're going to exceed the 4-rule (4 primary partitions or 3 primary + 1 extended).  One workaround there is to manually install Mint root in the remaining primary partition and mount the existing swap.

I bet Mint doesn't care if it resides in a primary or extended partition (as a logical).  Ubuntu sure does not.  If so, you can create a logical partition inside the existing extended and install unto that.  You can also mount swap as well.  In this workaround, you wont have to bother about primary partitions and that "darn" 4-rule.

regards,

PS.  swap is a bit big at 4GB.  But then again, with 500GB to work with .... that's less than 1%.  ;)

Also, if your intention is "just to try mint or other" ... why not just install virtualbox and virtualize those curiosities.  That way you don't mess with a good thing that you have right now.

---

### Post by annie227 on 2009-11-15
The 4 rule being 4 partitions to 1 hard drive?
I read about swap and wondered whether it should be reduced?

---

### Post by raymondh on 2009-11-15
> **annie227 said:**
> The 4 rule being 4 partitions to 1 hard drive?

Yes .....  4 primary partitions (or 3 primary + 1 extended) ..... per HD

---

### Post by Jon Monreal on 2009-11-15
How much RAM do you have? As a general rule swap = RAM is pretty good, but I think you're good with what you have.

I see you have two NTFS partitions. Which one is XP? What is the other used for?

At any rate, everything looks pretty good. Considering the fact that accessing NTFS partitions from Linux is generally much easier than accessing ext4 and the like from Windows, having a larger partition for Windows is probably a pretty good idea (and that's putting aside the bloat of some Windows programs).

---

### Post by annie227 on 2009-11-15
I have 2 GiB ram
sda1 ntfs is XP
sda2 ntfs is storage

---

### Post by annie227 on 2009-11-15
The thing is Ray,I did try virtualbox but haven't got a handle on it yet(so much learning).
One thing I've found with karmic so far is a few little annoyances like KDenlive and Kino for that matter closing down while trying to import files and other little glitches here and there.I have problems I didn't with jaunty so I have thought about going back to it(but would rather hang in until...at this stage),so I thought perhaps mint7 or even ubuntustudio 9.04,for something different though the sound part I wouldn't know how to use from reading and I'm not that keen,yet,just been watching

---

### Post by raymondh on 2009-11-15
> **annie227 said:**
> The thing is Ray,I did try virtualbox but haven't got a handle on it yet(so much learning).
One thing I've found with karmic so far is a few little annoyances like KDenlive and Kino for that matter closing down while trying to import files and other little glitches here and there.I have problems I didn't with jaunty so I have thought about going back to it(but would rather hang in until...at this stage),so I thought perhaps mint7 or even ubuntustudio 9.04,for something different though the sound part I wouldn't know how to use from reading and I'm not that keen,yet,just been watching

Ma'am ... am sorry to hear about your Karmic "challenges".  I have a test machine with Karmic but said machine has a 2nd HD with a working Jaunty install .... just in case.  And yes, though I have Karmic in "production" status in that machine, I still have to tweak a number of issues.  My laptops are kept in jaunty and Hardy patiently waiting for May - June 2010 when the next LTS comes out (I know it comes out in April, but I wait for about 4-6 weeks for the devs to iron out kinks before I actually install .... a practice I've broken in Karmic having seen/tweaked it since alpha).

Ok, back to the issue.  You could, as mentioned earlier, try to install mint as a logical partition inside the existing extended or, you use this effort to attack the virtualization learning curve.  My point being is that the more we work on partitions and the hd, the greater the risks of borking it. ... hence my suggestion to virtualize other distros whilst tweaking Karmic to your preference

You do have working back-up's, don't you?

---

### Post by annie227 on 2009-11-15
I did have a 160GiB HD I used for dual booting XP and Jaunty and it was brilliant but as soon as I put in the karmic disk,to my surprise it stated I had "imminent failure" of that disk(it had been making noises and needed defragg'ing in xp a lot) so sadly I moved to the 500 which was previously used in 2 partitions for my media storage.I have a 320GiB external which is just about full(until I delete multi copied files,duh) but I must say the loss of that 160 hurts.
I feel I'm wasting so much space with the 500 the way it is,hence wondering how to maximise it.
See how large my ubuntu and XP are?This is why I'm starting to investigate options and want optimum use/performance.Thanks so much for your help.
when you say working backups you mean backing up my data?oh yes,suffered there ONCE,never again!
Would you recommend me going back to Jaunty?I mean,that's what you've just said you are sticking with as a tried and true in the last reply.In the back of my mind,to be frank,I'm thinking it's the way to go,in the end saving time,hhhmm,I do miss my old install I had it just right.I got excited about the new release.
Hardy huh?Can you use the new apps with that?If you have time could you say what is the pros of hardy in your opinion?

---

### Post by raymondh on 2009-11-15
> **annie227 said:**
> 
Would you recommend me going back to Jaunty?I mean,that's what you've just said you are sticking with as a tried and true in the last reply.

I cannot recommend/suggest that as that will have to be a personal choice.

I keep Jaunty and Hardy because:

-   with the system/s I have, they are indeed tried and true.
-  They are working 99% of the time.  Well, jaunty is after some tweaking :)
-  I've played around with karmic since alpha and could not see the " big difference " vis-a-vis my current systems and hardware (which was supported in Jaunty).  But, being adventurous since version 7, I did install final Karmic on my test desktop.
-  I now appreciate the LTS  versions as truth be told, I am _now_ getting tired of tweaking every 6 months.  

I also have to admit that I have seen an occasion (a friends netbook) where Karmic was out-of-the-box-great as compared to his Jaunty install.  Then again, that was in his netbook.

I think your partitions are fine, Ms. Annie 227.  If any, I would consider separating /home from root (/).  But, you could do that if you decide to re-install later another version.   As for "maximizing' ..... remember that you have a 500GB and coming from 160GB.  I bet if you had 1TB you'd think the partitions are too small ;)  No offense meant, I think the partitions are fine as they are.  

Regards,

---

### Post by Miljet on 2009-11-15
One thing to think about is that if you install other operating systems, you WILL run into booting problems. Each new system will try to install its own version of GRUB which will overwrite your current version. You can install other systems without installing a new GRUB, but you will then have to manually add it to your existing GRUB. I've been there and done that. So if you are not willing to tinker with GRUB, don't install more than one Linux system.

---

### Post by raymondh on 2009-11-15
> **annie227 said:**
> 
Hardy huh?Can you use the new apps with that?If you have time could you say what is the pros of hardy in your opinion?

This is my personal opinion/observation.  I think that the 6-month release culminate in the next upcoming LTS.  The pros are added .... the cons are either fixed or not included. Of course, I have no proof hence the term "personal observation/opinion"

Here is a direct suggestion.  You challenge is to tweak Karmic and learn in the process.  It's a great learning opportunity.  If I were you, I'd join, peruse and browse launchpad. File a bug report about your 'X" crashing.  See if there are any fixes.  By the way, the developers hang out in launchpad..... ;)

Also check out the app's website to see if they have fixes for their app.

Regards,

---

### Post by annie227 on 2009-11-15
well thankyou Raymond.
The niggle I have about my 500 was that it was being used for storage only and I needed/need it so cutting into it hurt.It means I will have to at some stage buy another most likely.
I'd like to regain as much of that storage space as I can.
Thanks for your experience with OS's.much appreciated.

---

### Post by annie227 on 2009-11-15
Thanks miljet,i hadn't known that.
Some time ago I did install and have working xp,jaunty and mint7(I was and still am learning and was impetuous at times).it worked fine BUT,it may've been beginner's luck.
The first partition disaster I had was after I uninstalled the mint btw.I learned from that though,as one tends to.
Food for thought,thanks heaps

---

### Post by Dullstar on 2009-11-15
One the partitions on that drive is gonna have to go.  Sorry, you can only have 4 primary partitions or three primaries and 1 extended, from what I've read.  What you need to do is backup one, delete, and turn it into an extended.  Linux can be installed in a logical partition, don't worry.

---

### Post by raymondh on 2009-11-15
> **Dullstar said:**
> One the partitions on that drive is gonna have to go.  Sorry, you can only have 4 primary partitions or three primaries and 1 extended, from what I've read.  What you need to do is backup one, delete, and turn it into an extended.  Linux can be installed in a logical partition, don't worry.

Dullastar ... she has 2 primary partitions and 1 extended.  Swap is a  logical within the extended ... as well as Ubuntu.  She can, if she decides to, install another primary partition without sacrificing any existing.

---

### Post by annie227 on 2009-11-15
> **raymondhenson said:**
> Dullastar ... she has 2 primary partitions and 1 extended.  Swap is a  logical within the extended ... as well as Ubuntu.  She can, if she decides to, install another primary partition without sacrificing any existing.
I was concerned there and scrolling thru' the beginners guide..
Those 2 unallocated tiny spaces at each end-how can I incorporate (470.65MiB and 2.4GiB)them back into a partition(if possible)?
And if I decided to uninstal karmic and replace it with jaunty,IF,I'd just head for that partition,sda5?
And one other thing I've been intrigued about is hardy heron-with the long term support, that means all the updates keep up with new apps?
thanks for your valuable time,so,so,so appreciated

---

### Post by raymondh on 2009-11-16
> **annie227 said:**
> I was concerned there and scrolling thru' the beginners guide..
Those 2 unallocated tiny spaces at each end-how can I incorporate (470.65MiB and 2.4GiB)them back into a partition(if possible)?

[COLOR="Red"]
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Be careful. If any, I would extend the storage partition to the right.  I would also NOT MESS with sda1 (moving to the left just to gain 470mb) ... but that's just me.

Use a liveCD and in live session as that will unmount the partitions.  Gparted will not work on any partition that is mounted.  You'll know if you have a greyed-out option to resize.  Better yet, download and burn the latest gparted as a stand-alone live disc.[/COLOR]


And if I decided to uninstal karmic and replace it with jaunty,IF,I'd just head for that partition,sda5?

[COLOR="Red"]You will have to select manual (in step 4) > highlight the intended partition > edit > Use As > select mountpoint (root) > select file format > format.  Do the same for SWAP but just select SWAP FILE SYSTEM. In a jaunty fresh install, it overwrite the MBR and install GRUB legacy which is not a bad GRUB version.[/COLOR]

And one other thing I've been intrigued about is hardy heron-with the long term support, that means all the updates keep up with new apps?

[COLOR="Red"]You know, the next LTS is out in April 2010.... just a few months away. Anyway, to answer your question, yes my system is continuously updated .... as a simple example, I am running the latest pidgin in my hardy laptop.[/COLOR]



.

---

