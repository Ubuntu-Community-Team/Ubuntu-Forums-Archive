---
title: "Permission"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by Kellemora on 2010-02-18
I'm embarrassed!  You'll have to excuse this old man!
Tried the search feature and digging through all of my notes.
Ubuntu works so well I only need to get under the hood about 4 times a year so I forget how to do things.

I made several Q-CAD drawings for our home renovations.
Each were in a folder on my Desktop (copied to an external hard drive via rsync).  Not needing it I deleted the file on my desktop, forgetting it was the main file, so rsync did it's thing and removed it from the external drive, doh.  However, I lucked out and made a permanent copy that I now use on my desktop as a link to the permanent file, so I can delete it without problems and rsync keeps the copies safe.

OK - Here's my current problem:
We finished one renovation that I've had no problems opening the files.
Switched to a different file for a different room and I find I cannot open ANY of the files anymore.  Q-Cad reports "You don't have permission to open this file"!  I checked the permissions and it clearly shows my logged-in name with Full Permission - Group Read Only - Guest Read Only.
I checked each file one by one (right click, permissions) and they all have the correct permissions showing here.
Sadly, I don't remember how to get under the hood to check the RWX--XX, etc. area.  And with my luck, could really mess things up.

If this helps, the last time I had this problem, (and ths is what my notes tell me to do), I could Open Q-CAD FIRST then Open the file direct from Q-CAD, instead of just clicking on the file for it to open Q-CAD.
Problem is, this method is not working this time either.

Running Ubuntu 8.04 64bit version on dual core Athlon 5200.

Don't be hard on me, I just survived (I think) a heart attack, only home from the hospital 4 days ago.

TTUL
Gary

---

### Post by Kellemora on 2010-02-18
I'm marking this as solved since I found another workaround that let me open all the files again!

I copied the entire folder (not just a link) back to my desktop.
Opened Q-CAD and then accessed the folder on my desk.
All files opened FROM the Q-CAD File/Open button!
When I'm done, I'll copy the folder back so the changes are saved, rsync will take care of copying that to the off-site backup.

Still don't know WHY I don't have permissions to my own drawings when they reside anywhere other than on my own desktop though.
And why a Group member or Guest cannot open them Read Only as they are tagged.

TTUL
Gary

---

