---
title: "DVD/CD Players Not Recognized"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by rs321 on 2011-07-11
Howdy,

I'm a newbie who's simply trying to get my DVD and/or CD player(s) to work and to this end I have read the comprehensive posts and installed all the recommended stuff, all to no avail.  What I have been able to do is find that Ubuntu doesn't even know I have those players installed.  It knows I have a floppy drive and that's it.  How do I convince Ubuntu that I have that hardware?

-Randy

---

### Post by rs321 on 2011-07-11
Folks,

Took a fresh run at it this morning, due in part to no replies to the post because that is a sign that the problem is "pilot error" and not due to anything wrong with the system.  What I found was both the CD and DVD players are seen by Ubuntu but they both share common Properties symptoms:

Type, Size, Volume, Accessed, and Modified (from the properties list) were all Unknown.

Location was listed as Computer:///

Permissions could not be determined.

They are both set to Run With: Autorun Prompt.

I am such a newbie I'm at a loss as to what I should do next and the Help menu could have been written in Urdu for as much as I was able to get out of it.

Does anybody have any ideas as to what I should do next to make them function properly?

Thanks,

-Randy

---

### Post by AlphaLexman on 2011-07-11
> **rs321 said:**
> Type, Size, Volume, Accessed, and Modified (from the properties list) were all Unknown.

Location was listed as Computer:///

Permissions could not be determined.

They are both set to Run With: Autorun Prompt.
In my experience / opinion, 'Places -> Computer -> CD/DVD Drive' ...is **NOT** an accurate representation of the physical optical device. It is a _nautilus-only_ shortcut to familiarize windows users with a 'My Computer' equivalent.

The actual block device properties should be linked to /dev/cdrom or /dev/dvd but if you don't have an actual disk in the drive you may still get some unknown properties.

---

### Post by rs321 on 2011-07-11
AlphaLexman,

Thanks for the reply; sorry to take so long to get back but we're having intermittent T-storms this afternoon and my time here is sporadic.

You said the block device properties should be linked to /dev/cdrom.  I'm afraid I don't yet know how to do that.  What is the best way to go about it?

I installed wine and I'm sure that will help but was not the panacea I was hoping for.  It's taken me 2 1/2 days (maybe 15 hours) to get this far and I'll spend the time necessary to get it right but I'm groping blindly here.  Wine told me to include CD\DVD in permissions but I've found nothing yet on this forum in Search related to allowing permissions.

While I have you on the phone, so to speak, the system has told me that the Group for my CD is cdrom and Group ID is 24.  Are those the values I should enter in the CD Properties boxes?

Again, thanks for the tips.

-Randy

---

### Post by AlphaLexman on 2011-07-11
> **rs321 said:**
> AlphaLexman,

Thanks for the reply; sorry to take so long to get back but we're having intermittent T-storms this afternoon and my time here is sporadic.

You said the block device properties should be linked to /dev/cdrom.  I'm afraid I don't yet know how to do that.  What is the best way to go about it?

I installed wine and I'm sure that will help but was not the panacea I was hoping for.  It's taken me 2 1/2 days (maybe 15 hours) to get this far and I'll spend the time necessary to get it right but I'm groping blindly here.  Wine told me to include CD\DVD in permissions but I've found nothing yet on this forum in Search related to allowing permissions.

While I have you on the phone, so to speak, the system has told me that the Group for my CD is cdrom and Group ID is 24.  Are those the values I should enter in the CD Properties boxes?

Again, thanks for the tips.

-Randy

You shouldn't need **wine** to 'access / mount / read / write' your optical drives...

If wine can't find find them, but **ubuntu** can... that is a different issue. Please be specific.

Go to 'Places -> Computer -> File System -> dev' and right click on 'cdrom' then click properties...

Try it with and without a disc in the drive, you should see the differences.

FYI: group 24 is the default group for '**cdrom**' you shouldn't need to enter that value anywhere.

---

### Post by rs321 on 2011-07-11
AlphaLexman,

It was a miss, I'm afraid.  I was told that because I'm not the owner I cannot change permissions.  I honestly didn't think I was trying to change anything and just wanted to see what stuff said, but I am the owner and it wants to argue and I got nowhere with it.

Thanks again.  Maybe a restart will help the machine and maybe a beer will help me.

-Randy

---

### Post by AlphaLexman on 2011-07-11
> **rs321 said:**
> AlphaLexman,

It was a miss, I'm afraid.  I was told that because I'm not the owner I cannot change permissions.  I honestly didn't think I was trying to change anything and just wanted to see what stuff said, but I am the owner and it wants to argue and I got nowhere with it.

Thanks again.  Maybe a restart will help the machine and maybe a beer will help me.

-Randy
You should **NOT** be the owner of '/dev/cdrom' it should be **root** by default. 

What permissions are you trying to change, and to what ??

---

### Post by rs321 on 2011-07-11
AlphaLexman,

That's just it; I wasn't trying to change anything, just to look around.  I thought I saw my name listed as owner somewhere, which would make sense to me because I'm the only person on the machine.

I didn't have that beer I mentioned but I did hang a screen door.  Somehow it's just not the same, lol.  When I got back and re-booted the computer I put in a VCD to see if anything had changed because now *I don't have permission* to look into Movie Player.  Can't imagine what would happen if I actually had changed something.  I looked into Movie player because my CD player has the capacity to play DVDs and I was curious.  Replaced the VCD with an audio CD and the CD player seems to work fine now, and I thank you for that.

Okay, Root is the owner of /dev/cdrom, which is fine with me, and I'll try the same procedures to get the CD player to burn CDs because it has the physical capacity to do so.  Then I'll do a "laying on of the hands" to my DVD RW and hopefully get it straightened out, too.

Thank you again for getting me on the road.  I'll mark this thread as Solved after I tinker with the DVD.

-Randy

---

