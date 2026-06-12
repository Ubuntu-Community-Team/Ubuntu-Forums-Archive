---
title: "Suddenly: &quot;Unable to mount&quot;-&quot;Authentication is required&quot; on disk volumes."
date: 2009-12-09
forum: New to Ubuntu
---

### Post by emarkay on 2009-12-09
This is new, and I can't fix it - they worked fine last night.  4 volumes on 2 disks one is my Lucid test volume, the other 3 are NTFS.

I can't even see them in root (gksudo) Nautilus!

Rebooting does not help.

Any ideas?

---

### Post by emarkay on 2009-12-11
I have been away for 2 days and NO ONE has even a clue?  
I   even confirmed that there are no errors in the drives in Windows.
 
I am able to get to them by using the NTFS Configuration tool, but that is not Ubuntu native and was not needed previously.  
What has happened here?

---

### Post by mcdjork on 2009-12-11
Can you post your fdisk?

sudo fdisk -l

---

### Post by adbge on 2009-12-18
> **emarkay said:**
> I have been away for 2 days and NO ONE has even a clue?  
I   even confirmed that there are no errors in the drives in Windows.
 
I am able to get to them by using the NTFS Configuration tool, but that is not Ubuntu native and was not needed previously.  
What has happened here?

I had a similar problem after disabling unwanted start-up services. Have you changed anything under Preferences > Startup Applications ? If so, re enable everything and see if that fixes the issue.

If that doesn't work, try running ntfsfix.

---

### Post by Martin McFly on 2010-01-29
Also happens to me. However, I've been messing with startup services and this is result. Trial by fire I suppose, but it would be great to know how to fix it.

I'm joining to group of people with this problems then.

---

### Post by emarkay on 2010-01-29
Sorry, was real busy at end of year.  All OK now.

---

### Post by Shpongle on 2010-01-29
what solved your problem in the end just to help other users with similar issues ?

---

### Post by xflow on 2010-01-30
I would also like to know the solution.

---

### Post by bcummings on 2010-01-31
I had this problem as well.  I had a hard time figuring out the answer. The fix for me was fairly simple.  

In System --> Preferences --> Startup Applications I had been disabling some of programs.  It turns out that you need the PolicyKit Authentication Agent enabled.  This allowed me to mount the drives that I didn't have access to before.  I didn't realize that I needed that for drives located on the main system.  Once enabled it allowed me to authenticate and mount the drives.

---

### Post by Stoney Bird on 2010-02-02
For several months, I've been using Ubuntu in a dual-boot system with Windows Vista. Ubuntu and Windows are in two partitions on the boot disk. There is also an external disk drive where I put files that I want to be able to get at from both Windows and Ubuntu. This worked fine until this morning, when I began getting "Authentication required" messages when I tried to access the external drive from Ubuntu. The startup apps have not changed, so the PolicyKit Authentication Agent is still enabled.

Any thoughts?

---

### Post by danidemi on 2010-02-05
Yeah, very same problem for me. I used to mount the NTFS partition without a single problem until this morning. Now I start getting the "Authentication required" pop up.

---

### Post by brokenleg on 2010-02-05
I checked if PolicyKit Authentication Agent on and it was on.

There should be another reason.  Anyone solved this problem yet? 

In System --> Preferences --> Startup Applications I had been disabling some of programs. It turns out that you need the PolicyKit Authentication Agent enabled. This allowed me to mount the drives that I didn't have access to before. I didn't realize that I needed that for drives located on the main system. Once enabled it allowed me to authenticate and mount the drives.

---

### Post by brokenleg on 2010-02-06
Finally found the way to fix this problem.  :)  

Do the following :)



Got this info from : [http://rayslinux.blogspot.com/2009/12/authentication-is-required-to-mount.html](http://rayslinux.blogspot.com/2009/12/authentication-is-required-to-mount.html)


Use Terminal and:

sudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

Find the id:
org.freedesktop.devicekit.disks.filesystem-mount-system-internal

Look for the line:
'allow_active'auth_admin_keep'/allow_active'
and replace it with:
'allow_active'yes'/allow_active'
*Sorry the < character is being interpreted by blogger so it has been changed to '*

And save!


Have fun!

---

### Post by And1945 on 2010-02-19
> **brokenleg said:**
> Finally found the way to fix this problem.  :)  

Do the following :)



Got this info from : [http://rayslinux.blogspot.com/2009/12/authentication-is-required-to-mount.html](http://rayslinux.blogspot.com/2009/12/authentication-is-required-to-mount.html)


Use Terminal and:

sudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

Find the id:
org.freedesktop.devicekit.disks.filesystem-mount-system-internal

Look for the line:
'allow_active'auth_admin_keep'/allow_active'
and replace it with:
'allow_active'yes'/allow_active'
*Sorry the < character is being interpreted by blogger so it has been changed to '*

And save!


Have fun!
I love you...

---

### Post by And1945 on 2010-02-20
Strange, this only works until reboot ...

---

### Post by migel_wimtore on 2010-03-09
Great fix brokenleg. This did the trick for me (and held after reboot), though i am no longer asked for my password when i select to mount my OS X partition via nautilus, but this is an improvement.

Cheers.

---

### Post by Bogdon6 on 2010-03-13
I hear you. I keep trying Ubuntu, but it's not a user-friendly operating system. And if Ubuntu isn't, then what linux OS is?

---

### Post by drreid on 2010-04-05
Hey All,

I've got the same problem on kubutu 9.10 and tried the solutions posted above but like someone else above the fix doesn't survive a reboot.  I've tried making similar edits to :

/home/drreid/.kde/share/config/policykit-kderc
/usr/share/PolicyKit/policy/org.freedesktop.policykit.policy
/usr/share/polkit-1/actions/org.freedesktop.policykit.policy

but still no luck.

---

### Post by mc4man on 2010-04-05
> but like someone else above the fix doesn't survive a reboot.
The edit described should work, and survive a reboot (but not an update to devicekit-disks
So maybe it's a kubuntu thing...

Anyway for karmic I prefer this method which will survive an update, you may want to give it a go.

I'd suggest you undo your edits (editing these files willy-nilly is not recommended

You could at the very least reinstall devicekit-disks which will overwrite any edits you made there.

```
sudo apt-get --reinstall install devicekit-disks
```

Then follow as described here - 2 simple steps - use copy and paste

[http://ubuntuforums.org/showthread.php?p=9071501#post9071501](http://ubuntuforums.org/showthread.php?p=9071501#post9071501)

---

### Post by drreid on 2010-04-06
Thanks for the effort mc4man.  I tried your fix. but I am still asked for the admin password.

---

### Post by nimesh2402 on 2010-04-10
Hey, I still have the issue of not mounting the Disk..Can any one help me out?
I will provide details if needed...


Thanks in advance...

---

### Post by drreid on 2010-04-16
Thanks mc4man.  I tried it again and this time it's working.

---

### Post by thiyagi on 2011-12-05
thank you..

---

