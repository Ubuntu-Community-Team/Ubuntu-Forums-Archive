---
title: "Operating system not found"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by maxwinter2001 on 2010-01-15
I am not a techie.  I don't know what 90% of the abbreviations, programs, etc. mean or are about.  So if anyone can help me out, please feel free to condescend.  

I've had trouble installing Ubuntu for the last three days.  My laptop recently caught the Rogue Internet Security 2010 malware bug.   While trying to get rid of it I rebooted a couple of times.  The second time I could not log in.   The bug had taken away my ability to do so.  I have no money and could not take the machine to be wiped and the software (Windows 2000 Professional, Office 2003), reinstalled, so I decided to wipe the drive myself by installing a Windows XP disc I had.  ¾ of the way through it got to the product key question, and for some reason insisted that the key I have is invalid, (maybe because it’s been used before on another computer?  I don’t know).  

Since, as mentioned above, I am broke, I got to looking up free OS’s and ran across Ubuntu.  It sounded ideal so I downloaded it on a friend’s computer, burned a Live CD, and inserted the disc into my laptop, (with the help of some folks in this forum).  I did the memory test: good. Had it check the disc for defects: none.  So I told it to install.  It got 34% done and then froze.  I was told by someone in this forum to try Alt-PrintScreen followed by inputting the letters R-E-I-S-U-B.  That did not do anything so the same person told me to unplug and try again.  I not only did that, but over the last few days I have (1) Burned another Live CD and tried it; (2) made one for Kubuntu and tried it, and (3) messed around with various settings in the Setup Center, (they're all back at default now).

That first 34% was the closest I ever got to getting Ubuntu loaded -- until today.  During most of the last few days of attempting to load it would not even get to the desktop to start installing.  Usually it would stick at one point or another in the setup? DOS?  whatever, screen, (black screen & white writing).  I saw multiple times "Error" something something "logical block" something something, and a bunch of numbers.  There would be two of these messages,(with the same two six or seven digit numbers at the end), repeated multiple times before it would quit, presumably waiting for me to give it a command.  Not knowing what to do I would reboot and try it again.  Sometimes I'd wind up with that screen again, sometimes with the same kind of screen, but which said Error, defect in disk, something something.  I don't know for sure, but since the hard drive was replaced with a new one a year ago, I'm assuming any defects came from the Rogue Internet Security 2010 bug.

Each time I'd try the Live CD again I would have to start from scratch.  Today, I made it to the desktop and startsd the "install" process again.  This time though, when it asked about partitioning, I had it partition off one third of the disk for the parts of Ubuntu that had previously been loaded.  I had previously -- the only other 2 times I made it this far -- been telling it to erase and use the whole disc.  Sure enough this worked (did it avoid the defect in the disk this way?  I don't know), it finally loaded 100%.  

HOWEVER, once I, followng it's instructions, removed the CD for the reboot, all I got, (and continue to get), is "Operating System not found."  HELP PLEASE!

---

### Post by nitstorm on 2010-01-15
i am not sure about the problem, but when you do a direct download of the cd image it might miss a few parts, you'll have to check the md5sum and all... best is to download a torrent of the cd-image and then burn it onto a disc, and then try installing from it. hope that helped, if not i am sorry..

---

### Post by Sef on 2010-01-15
Instead of installing, go down to 'check disk for errors' (or somethng similar.) If that is ok, then see if you can run the Live CD.  Report back what happens.

---

### Post by maxwinter2001 on 2010-01-15
nitstorm and Sef: Thank you both for your replies, however
nitstorm: I have no idea what three quarters of your reply means
and 
Sef:  As I said originally: " I did the memory test: good. Had it check the disc for defects: none. So I told it to install."

---

### Post by lemmy999 on 2010-01-15
Max- does the disk boot so that you can use it as a live CD?

---

### Post by maxwinter2001 on 2010-01-15
yes, it wasn't til after I pulled it out for the reboot by the newly loaded Ubuntu, that it started say Operating System not found.

---

### Post by maxwinter2001 on 2010-01-15
As noted in my original thread entry: "I had it partition off one third of the disk for the parts of Ubuntu that had previously been loaded."  Could it be that, even though 100% of Ubuntu got loaded onto 2/3 of the disc, the machine is still looking at the first part of the disc, i.e., the first third that only has part of Ubuntu loaded onto it, when it's looking for an OS?  If so, what do I do to make it look at the part of the HD that has all of Ubuntu loaded on it when it first powers up?  (And if that theory is not correct, what else can I do?  As I said originally, I'm not a techie, so I'm just grasping at straws here.)

---

### Post by albert s on 2010-01-15
can you boot the live CD again,
then try and install it and let it use the whole disc this time,
simply use guided partitioning.
perhaps there is something corrupt on the portion of HDD where you think the original install is that is trying to boot first.

---

### Post by maxwinter2001 on 2010-01-16
albert: I really appreciate your suggestion.  And I may do that.  But first, how sure are you about this?  Remember, I tried to load  this several times.  Only 3 times did I make it even to the desktop, not counting this last one.  And those three times I DID have it erase all and use the whole disc.  At those times it always crashed at 34% completion of install.  It was not until I told it to partition off the first third of the disc and only use the other 2/3 that it finally loaded 100%.

---

### Post by maxwinter2001 on 2010-01-16
Anyone else have an opinion on this?

---

