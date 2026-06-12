---
title: "Can't sync Thunderbird on dual-boot with XP"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by noob555 on 2009-01-09
Hello everyone,

I recently loaded ubuntu 8.10 alongside XP in a standard dual-boot setup.  Since my mail and calendar are through thunderbird with the lightening extension, I follow the directions of mozillazine that tell me how to sync my ubuntu thunderbird with the profile on my XP drive.  Basically, it says to simply create a profile through the profile manager that directs straight to the profile that already exists.  Simple enough.  And when I load it, my mail works like a snap.

Here's the *problem*.  It only works the first time.  Whenever I shutdown and reload, I get an error message stating that thunderbird is "already open and not responding."  basically, the computer tells me to shut down thunderbird before I can open a new window *even though thunderbird is NOT open*.  Any thoughts on how to fix this problem?  Is it even possible to fully sync these profiles?

---

### Post by kellemes on 2009-01-09
Have you read [this]("http://kb.mozillazine.org/Profile_in_use")?
You need to delete 1 or 2 lock-files.
Never forget to backup your profile just in case.

I had this sometimes when I shared my Thunderbird-profile across os's.
Could be it has to do with different versions of Thunderbird maybe?

Personally I dumpt Thunderbird all together and imported all my accounts to gmail, that's the ultimate solution for cross-platform mailing.
Now I only use Thunderbird to create a local backup of my gmail-data ones in a while.

Good luck.

---

### Post by noob555 on 2009-01-09
Thanks for the link!  :)

That's definitely the error message that I am receiving.  And based upon the content of the article, I'm guessing that the problem is an issue of access rights because I remember one of the mozillazine articles stating that syncing directly to the windows drive would create read-only access.

I agree that just using gmail directly is the ultimate cross-platform solution, but that's no good for me because some of my emails are rather confidential and I don't feel comfortable with them just sitting on the gmail public servers indefinitely.

Do you think that creating a shared drive for the XP/ubuntu system to hold the profile would be the solution?  Any experience with that?

---

### Post by kellemes on 2009-01-09
> **noob555 said:**
> (..) Do you think that creating a shared drive for the XP/ubuntu system to hold the profile would be the solution?  Any experience with that?

That's what I always did actually..
I have a FAT32 partition just for stuff like this. Although other filesystem-formats can be chosen.
Just one Profile-folder on this partition/drive and point to it using "thunderbird -profilemanager" from both Tux and Win, works fine.

---

### Post by noob555 on 2009-01-09
Awesome.  Thanks!

---

