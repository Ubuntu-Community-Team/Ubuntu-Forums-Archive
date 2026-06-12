---
title: "Issue Syncing Profiles Between Gutsy Gibbon / XP MCE"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by romphill on 2008-12-18
I've recently changed back and forth between gutsy gibbon and opensuse to dual with XP on my laptop, and am now having some issues in gutsy getting file sharing back up and running.

I'm trying to share 1 profile for firefox between ubuntu and windows.  right now i have a 30 gig partition for linux and a 120 for windows.  I currently have the firefox profile working on windows, and used profile manager to use that profile in ubuntu.  it immediately worked on ubuntu, so i rebooted with windows.  it worked there so i was happy, and then rebooted into linux.

unfortunately when i got back into ubuntu, it tells me i have another instance of firefox running and won't let me open the program up.


any ideas?

---

### Post by anim on 2008-12-18
delete the file(s) (From the profile directory)
# "parent.lock" (Windows), or 
# "lock" and ".parentlock" (Linux)

What probably happened was that firefox did not shutdown correctly when you rebooted XP and the firefox profile remained locked.

---

### Post by romphill on 2008-12-19
Thanks for the quick reply, but that doesn't solve the issue.  Firefox still works just fine in Windows, but gives me the still running error in linux.

---

### Post by romphill on 2008-12-20
bump bumpy

---

### Post by romphill on 2008-12-24
> **romphill said:**
> I've recently changed back and forth between gutsy gibbon and opensuse to dual with XP on my laptop, and am now having some issues in gutsy getting file sharing back up and running.

I'm trying to share 1 profile for firefox between ubuntu and windows.  right now i have a 30 gig partition for linux and a 120 for windows.  I currently have the firefox profile working on windows, and used profile manager to use that profile in ubuntu.  it immediately worked on ubuntu, so i rebooted with windows.  it worked there so i was happy, and then rebooted into linux.

unfortunately when i got back into ubuntu, it tells me i have another instance of firefox running and won't let me open the program up.


any ideas?

Any help would be incredibly appreciated!

---

