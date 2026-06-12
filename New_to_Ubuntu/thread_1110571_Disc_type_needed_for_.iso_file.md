---
title: "Disc type needed for .iso file?"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by blue.aether on 2009-03-29
Sorry to be asking such a lame-brain question, but I almost never do anything with physical discs.

When burning the .iso file needed to get started with a dual-boot, do I need to burn the file to a data CD?  Or will a music CD be OK for this?

Normally, I'd assume that anything important would go on a data CD, but all I've got on hand are blank music CDs, and I'm impatient to get started.

Thanks,

Andy

---

### Post by linuxuser21 on 2009-03-29
Yeah, any CD will work.  If it's over 700mb though, you're going to need a DVD.

---

### Post by Vendettaseve on 2009-03-29
Reread the OP, I gave useless advice :D

---

### Post by talsemgeest on 2009-03-30
As long as the iso file is under 700mb, it should work on any blank cd. Just make sure you burn it as an iso, and not just burn the iso file as a file.

---

### Post by hyper_ch on 2009-03-30
you need to burn it as "image". Your burning program should have an option like that somewhere. It's not data and not music.

---

### Post by CatKiller on 2009-03-30
> **blue.aether said:**
> When burning the .iso file needed to get started with a dual-boot, do I need to burn the file to a data CD?  Or will a music CD be OK for this?

"Music" CD-Rs are exactly the same as "data" CD-Rs, but more expensive. Buying a "music" CD-R pays a tithe to the royalty collection agencies to compensate for the fact that you're "obviously" using it for large-scale commercial copyright infringement :rolleyes: "Music" CD-Rs have a flag set to say that you've paid the tithe, and some stand-alone CD burners (older professional ones, usually) require this flag to be set before you can use them. Other than that, "music" CD-Rs are a waste of money. But they will work fine for all other purposes too.

---

### Post by blue.aether on 2009-03-30
Thanks for the replies here.

I will go ahead and burn the ubuntu .iso file (as an image) onto one of my blank CDs.  I'm psyched!

The info I got here was what I needed to clear up my confusion regarding audio CDs and data CDs.

I've been reading over my notes (from way back), and I see now that I had misunderstood what I'd been told by my brother regarding the different CDs.  (My brother is both an accomplished programmer and an audiophile, so I trust him on these things.  But he only answers my questions so many times before he refers me to Google!)

What my brother had been trying to explain to me was that, when I burned an audio CD, I was asking the burner to do something different than when I burned a data CD.  An audio CD I burned would include a table of contents of some sort plus the song tracks.  But a data CD would be burned with **error correction**.  And *that* was the big deal my brother was trying to impress upon me.

ANYway, . . . I will burn the ubuntu disc as an .iso file.  Thanks.

Andy

---

### Post by lkraemer on 2009-03-30
Dual Boot......Well, that certainly is one way to go, but you will
find that after you use Linux for a while you won't boot that other
OS.  Another way to go is to install VirtualBox, and then make a smaller
Windows install on a 15 or 20 Gig Virtual Disk Image (VDI), just for
those moments you MUST HAVE your Wonders FIX!.......YUK!

Either way this Dual Boot site is good reading:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Go visit this site and read about making a dual boot system,
and how to use SuperGrub.

Then when you partition the drive give XP enough to run since
you will rely on this until you are fully converted to Linux.
You can ONLY have 4 Primary Partitions. The first one being XP,
and the following three UBUNTU (/root /home /swap) versus
making one large partiton along with the swap. This will allow
you to wipe the Root partition and not loose any of your data
that is in /home. Just a suggestion..... or just make one Linux
EXT3 Partition.

XP Should be installed first, then Linux, as Linux doesn't care if
another OS is installed, unlike Wonders.

/swap ~2X RAM Size
/home ~60 Meg more or less  EXT3
/ ~20 Meg more or less = ROOT Partition  EXT3
Windows 40 to 60 Meg more or less  NTFS

Also, go download SuperGrub and learn how to use it to restore
your MBR as you will need it down the road.

And you might as well get the LiveCD's of:
Ultimate Boot CD
Clonezilla
Gparted
System Rescue CD

Now download the LiveCD's of Ubuntu, PCLinuxOS 2009.1, sidux, Puppy,
and others of your choice.  Verify the MD5SUM's of your downloaded ISO's,
Burn as Disk at Once (DAO) and at 4x or 8x on good media.  Now you're
ready for testing your distro's to see what fits your needs and likes,
and what works out of the box and what doesn't.  (There is Windows
software to verify the ISO MD5SUM, and Nero will burn the ISO.)

[http://distrowatch.com](http://distrowatch.com) is a good site to check out the distros, and
you will find that you will visit it each day to see what is going on.

Make a List of MUST HAVE Windows software that would keep you from
switching to Linux.  Most Windows programs have Linux replacements,
or can be run with WINE, CROSSOVER, or VIRTUALBOX running XP.

lkraemer

---

### Post by blue.aether on 2009-03-31
lkraemer, THANK YOU.  A fantastically helpful posting for me, and the hermanzone link you suggested is the best I've seen yet for what I'm doing.  It will take me some time to work through all of the material there, but I'd rather take the time up front and the proceed with more assurance later on.

I'm working on all of the other downloads you listed, too.  But, even there, it takes me a bit of time to sort out all of the Google links!  Just a lot of new info for me here.

As for my migrating to ubuntu from Wonders, NOBODY would be happier about that than me.  My fantasy is that ubuntu will be to Wonders what Firefox has been to IE.

I keep hearing about how ubuntu and the other Linux distros are no way ready for the Big Time--and these comments are coming the same brother mentioned above, a guy who actually *uses* some of the distros (Red Hat and another) alongside Unix at work.  He also has installed versions of all of the current Windows and Mac OS.  (And, yes, I really do mean all of them.  The guy loves seeing what's being done with new OS software.)

But, . . . this is the same guy who opts to use IE instead of the Fox because he *has* to use IE for a number of tasks at work.  And because most of the people he works with use IE, and he prefers to stick with just one OS, just to keep life a bit simpler.

So I'm hoping that, in the same way that I use Firefox while my brother uses IE, I will be able to use ubuntu, even though he cannot use it himself.  (Maybe his idea of the Big Time is whether or not he can use ubuntu himself?)

I love Firefox.  And I can't stand Microsoft.  (I should get a quote of Gates' public talk when he explained that quality coding was not necessary because the improvements in hardware speed would always be ahead of the software, so the fast hardware could compensate for slow code.)  So I'm a good candidate for ubuntu.

Thanks for the info.  I'll post again when I've got ubuntu on my system, but that may be a while, so don't wonder if I gave up on ubuntu.

Andy

PS:  What's with the log-in for this site?  When I go the log-in page, I find the User Name box with "User Name" already showing in the box, but I cannot write over it to log in.  The only way I can log-in is to reply to a posting.  I'm then taken to a different log-in page that has working boxes for User Name and Password.  Anybody know what's going on with this?  A.

---

### Post by lkraemer on 2009-03-31
Good Luck.................Remember, you didn't become a Wonder's
expert overnight.  He slowly migrated money from your wallet as he
led you through the Vaporware upgrades, Security patches, and
Antivirus upgrades all to sell more software to his followers.

This trip will be exiting, as he doesn't have any more CONTROL!
You have it ALL!

lkraemer

---

### Post by mlentink on 2009-03-31
> **lkraemer said:**
> Good Luck.................Remember, you didn't become a Wonder's
expert overnight.  He slowly migrated money from your wallet as he
led you through the Vaporware upgrades, Security patches, and
Antivirus upgrades all to sell more software to his followers.

This trip will be exiting, as he doesn't have any more CONTROL!
You have it ALL!

lkraemer


chill,  dude

---

### Post by blue.aether on 2009-03-31
Chill, you say?

Well, yes, I'm sure you know best.

I suppose one could argue the point that the world could never have too many calm, orderly, properly-disciplined, well-behaved, predictable citizens.

And, certainly, we have a proud history of working towards the goal of well-chilled citizenry.  So many examples.  Even the medical community took a turn and contributed towards the cause of good citizenship with their development of effective lobotomy techniques.

And, if nothing else, none can question the fact that a pacific, well-chilled citizenry has always been an essential component in the success of Big Blue.

On a personal level, . . . I confess that I sometimes entertain different thoughts on this subject.  And I know that not everybody would consider me a model citizen.  But I do try--on a daily basis, actually--to repress my bad attitudes.  And to hide the decadent behaviors.  And, of course, above all else, keep myself properly chilled.

And, yes, I've been going to group.  You know, as in, . . . "Hi.  My name is Andy, and I'm a compulsive Microphobe.  But thanks to the support of my MVP Sponsor and this well-behaved group, I've been successful in Kissing Big Blue's Butt now for 73 days, 8 hours, and 27 consecutive minutes.  I know I could not have done it--not kept myself properly chilled without your guidance and support.  I am so looking forward to earning my 90-day pin for Big Blue Butt-Kissing!"

So, yes, we'd better chill.

---

### Post by talsemgeest on 2009-03-31
> **blue.aether said:**
> Chill, you say?

Well, yes, I'm sure you know best.

I suppose one could argue the point that the world could never have too many calm, orderly, properly-disciplined, well-behaved, predictable citizens.

And, certainly, we have a proud history of working towards the goal of well-chilled citizenry.  So many examples.  Even the medical community took a turn and contributed towards the cause of good citizenship with their development of effective lobotomy techniques.

And, if nothing else, none can question the fact that a pacific, well-chilled citizenry has always been an essential component in the success of Big Blue.

On a personal level, . . . I confess that I sometimes entertain different thoughts on this subject.  And I know that not everybody would consider me a model citizen.  But I do try--on a daily basis, actually--to repress my bad attitudes.  And to hide the decadent behaviors.  And, of course, above all else, keep myself properly chilled.

And, yes, I've been going to group.  You know, as in, . . . "Hi.  My name is Andy, and I'm a compulsive Microphobe.  But thanks to the support of my MVP Sponsor and this well-behaved group, I've been successful in Kissing Big Blue's Butt now for 73 days, 8 hours, and 27 consecutive minutes.  I know I could not have done it--not kept myself properly chilled without your guidance and support.  I am so looking forward to earning my 90-day pin for Big Blue Butt-Kissing!"

So, yes, we'd better chill.
Nicely said, blue.aether. :)

---

