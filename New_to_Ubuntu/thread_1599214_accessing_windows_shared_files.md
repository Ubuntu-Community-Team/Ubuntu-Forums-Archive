---
title: "accessing windows shared files"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by ianb72 on 2010-10-17
I have been away from Linux and Ubuntu for a while now so I've forgotten things.
Anyway I have duad booted my windoze XP home and Ubuntu 10.04 LTS, well I can not seem to access the shared files on the windows partition of the hard drive, I can get it displayed in the **Places** > **Network** but when I click on it I get > **Unable to mount location**
 Failed to retrieve share list from server

Any ideas on how to get these files, as it will take far too many CD's or DVD's

Cheers
Ian

---

### Post by Verbeck on 2010-10-17
searched the forums and found this:

[http://ubuntuforums.org/showpost.php?p=8571046&postcount=9](http://ubuntuforums.org/showpost.php?p=8571046&postcount=9)

---

### Post by ianb72 on 2010-10-17
> **Verbeck said:**
> searched the forums and found this:

[http://ubuntuforums.org/showpost.php?p=8571046&postcount=9](http://ubuntuforums.org/showpost.php?p=8571046&postcount=9)
That didn't seem to work, as now I can't see the folder at all!

---

### Post by Mark Phelps on 2010-10-18
Sorry, confused by your original post ...

You say you have a multi-boot machine, presumably with separate partitions on the same box, for Ubuntu and for MS Windows.  Right so far?

And, you're trying to access the MS Windows partition using a network mount?  That's the confusing part.

If they're on the same machine, you should simply be able to double-click on the partition Icon in Places and open Nautilus with access to those files.

---

### Post by ianb72 on 2010-10-18
> **Mark Phelps said:**
> Sorry, confused by your original post ...

You say you have a multi-boot machine, presumably with separate partitions on the same box, for Ubuntu and for MS Windows.  Right so far? **Yeah I just installed Ubuntu within Windozes**

And, you're trying to access the MS Windows partition using a network mount?  That's the confusing part.

If they're on the same machine, you should simply be able to double-click on the partition Icon in Places and open Nautilus with access to those files.

[B]I have tried that, even tried re-naming the windows system to MSHOME2 WINDOZE so not to confuse it with any other computer in the house but still not joy, oh I have even turned the firewall off, but I can access my XP laptop and the wife's Vista laptop no problems, never had any problems like this before.
Like you said I've just clicked on the windows partition and accessed the files!! [/B]

---

### Post by Mark Phelps on 2010-10-18
OK, if you have Ubuntu installed within Windows, that is known as a Wubi-based install -- in which a single file is created on your Windows partition and Ubuntu is run using that.

The MS Windows filesystem in that situation can be found at "/host".

---

