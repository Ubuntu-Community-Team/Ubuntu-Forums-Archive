---
title: "How tricky is it to resize both XP and Ubuntu partitions without reinstalling either?"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by Vunutus on 2009-04-09
I believe I'm ready to start weening myself off Windows some more. I already run only Ubuntu on my laptop and find myself rarely ever using Windows on my desktop now that I bought a 360 to play games with.

My current 250GB drive is set up roughly like this:

150GB Windows XP
50GB Ubuntu
50GB NTFS partition used to share music, videos, TV and such across operating systems.

The 50GB for Ubuntu is starting to get a little bit cramped (especially when messing around with VirtualBox). I'd like to change it to something more like 100GB for each OS, but I don't want to reinstall either. 

I don't forsee Ubuntu having too many problems when it comes to resizing, but I don't think XP would handle it very well. Are there any guides for this sort of thing, as well as program recommendations?

---

### Post by Sidewinder1 on 2009-04-09
Can't really give you a step by step but it should work OK. Just remember to **defrag the NTFS partitions** before shrinking or resizing.
HTH
Side
PS Backup anything that you can't afford to loose. :-)

---

### Post by eeperson on 2009-04-09
I would recommend using gparted from the live CD.  It is pretty easy to do.  As mentioned before, I think you need to defrag your NTFS partitions you want to shrink(although I am not sure about that since I haven't done it myself).  Also, make sure that you back up any important data.

---

### Post by presence1960 on 2009-04-09
> **Vunutus said:**
> I believe I'm ready to start weening myself off Windows some more. I already run only Ubuntu on my laptop and find myself rarely ever using Windows on my desktop now that I bought a 360 to play games with.

My current 250GB drive is set up roughly like this:

150GB Windows XP
50GB Ubuntu
50GB NTFS partition used to share music, videos, TV and such across operating systems.

The 50GB for Ubuntu is starting to get a little bit cramped (especially when messing around with VirtualBox). I'd like to change it to something more like 100GB for each OS, but I don't want to reinstall either. 

I don't forsee Ubuntu having too many problems when it comes to resizing, but I don't think XP would handle it very well. Are there any guides for this sort of thing, as well as program recommendations?

Have successfully shrunk and added space to both windows and ubuntu partitions without reinstalling with both the Ubuntu Live CD and the Gparted Live CD. As others have said defrag windows and _always back up your data_ While the partitioner works great there is always the odd chance something may go wrong when manipulating your partitions. To sum it up : stuff happens! Don't get caught with your pants down.

---

### Post by Shpongle on 2009-04-09
if you dont use xp for heavy apps, you could always just make a dynamic partition in virtual box, thats what i have and it works great. i can work between the two seemlessly, also youll have a full disk for ubuntu and your media ect, you can also set up a shared folder between the 2 os's to transfer files , this is really handy. it works well for me

but to each his own . . . its all about freedom of choice

---

### Post by st33med on 2009-04-09
> **Sidewinder1 said:**
> Can't really give you a step by step but it should work OK. Just remember to **defrag the NTFS partitions** before shrinking or resizing.
HTH
Side
PS Backup anything that you can't afford to loose. :-)

Adding on to this, do not repartition more than half of an NTFS drive.

---

