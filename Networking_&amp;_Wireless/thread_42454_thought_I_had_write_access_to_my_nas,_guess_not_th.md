---
title: "thought I had write access to my nas, guess not though...."
date: 2005-06-17
forum: Networking &amp; Wireless
---

### Post by spudley on 2005-06-17
Ok, I thought I was on the right track (yes, I'm a Linux newbie).

I have a NAS box (runs linux) here that works 100% for all my machines - varied from w2k, xp and Ubuntu systems.

All was good with all my machines reading & writing to it, except for my Ubuntu machines when I added a new user.  My 'orginal' install user has read/write access, but my new users don't.

Here is what I did to get things working to begin with on my Ubunto workstations:

1) install samba
2) install smbfs

(I have _not_ added any users to samba at this point)

3) My fstab was amended with this:
*//nas-media/disk1 	/media/r 	smbfs 	username=xyz,password=123,workgroup=abc,uid=theboss   0	  0*
(odd, there is a space inserting in 'theboss' above (between the s and s), which really is not in my fstab file)

That worked great... my install user id for Ubuntu was 'theboss' and I have read/write access to an "R" folder/directory on my Ubuntu desktop now.

Well, I added another user 'staff'.  I then made a group 'nasusers', added 'theboss' and 'staff' to the group 'nasusers' and changed my fstab entry from uid=theboss to *gid=nasusers*

Now, login with 'theboss' still has RW access to my nas box, but 'staff' is read only.

I'm stumped... I have not exhausted things to do, but I don't want to do dozens of steps to end up fixing the problem, but not really know what minimal steps are required to get it all working - as I change from XP & w2k to Ubuntu systems, I'd like the install as quick & 'effortless' as possible.

Thanks for any assistance!

---

