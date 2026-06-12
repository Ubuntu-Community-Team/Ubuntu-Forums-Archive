---
title: "Installer partitioner makes irrational size choice"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by porphyrula on 2009-07-20
My disk has one Windopws XP partition of 80GB and another 80GB of unallocated space.  I wanted to install ubuntu in the unallocated space.

Based upon the many web articles insisting that this was an "easy" process, I ran install from 9.04 live and chose the dual boot option.  The installer proceeded to resize my Windows partition to take up almost the entire disk, and squeezed ubuntu into a couple of tiny partitions at the end.  It gave me NO chance to specify partition sizes.  The result is that the installer runs out of room on the disk and Ubuntu does not boot correctly, and my Windows partition is now much bigger than I want.

---

### Post by Yvan300 on 2009-07-20
Run the  install again and this time choose manual when the partitioner comes up. It is a little more advanced but is very flexible. All you have to do is specify the sizes for the disk and then choose the mount points and the swap partition yourself. This is as easy as clicking a button, if you are unsure of the persedure, ask and i will explain in more detail.

Good luck !

---

### Post by porphyrula on 2009-07-20
Thanks, I understand that I can make the partition choices manually.  My point was from the viewpoint of a user the behavior I was seeing indicates either a bug or some very odd assumptions on the part of the software developers.
 
I have to assume that this particular install option must work smoothly for almost everyone else, and I'm curious to know why it fails for me.
 
I guess I should have posted this in a bug reporting forum - forgive me, I'm new around here!
 
Thanks for your help.  I'm going to keep trying the other option to see if there's something procedural I can vary that makes a difference.

---

### Post by Yvan300 on 2009-07-20
Everyone's hardware is different to some extent. Ubuntu works perfectly on my laptop, yet when  i tried to install it on a friend's the partitioner did not load. And yes most likely it is a bug and you should report it (if one has not been filed already) so that others to come may have a smooth install experience.

---

### Post by Bartender on 2009-07-20
I think you're shooting from the hip.  Probably the Ubuntu installer was unable to wedge some part of your Windows install out of the way and had to settle for a less-than-optimal sizing. 

In other words, blame Microsoft, not the Ubuntu installer.  Considering the automatic installer has worked fine for thousands of people, it's premature to start yelling about a bug based on one case.

---

### Post by porphyrula on 2009-07-21
Defensive, defensive, defensive!
 
No-one is more happy to blame Microsoft for things than I am, but clearly this problem is not their fault.  The ubuntu installer did not need to "wedge windows out of the way" because there was plenty of free space outside of the Windows partition.
 
As a professional software developer of many years standing, I can attest that if software I write works for "thousands of people" but fails for just one, then my software is NOT correct.
 
After trying the procedure 3 times with the same failure, I decided to just specify the partitions manually, which DID work as expected, although now my GRUB menu has 4 instances of ubuntu listed!
 
Thanks for everyone's help!

---

