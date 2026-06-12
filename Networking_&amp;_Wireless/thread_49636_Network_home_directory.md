---
title: "Network home directory"
date: 2005-07-17
forum: Networking &amp; Wireless
---

### Post by RicJD on 2005-07-17
I'm thining of making my home directory reside on one machine which will be access from all my computers (well just my desktop and laptop).  Basically  I will be having a server which is on all the time, and my home directory would point to this.

Has anyone done this, or tried to do this?  Is there anything I need to think of?  I was hoping it would be as simple as putting 'server:/home_directory      /home' in my fstab. Am I correct?

The only thing I was really worried about is the speed lost from loading up from netowrk, but I only used 7,200 rpm IDE hard drives, and my network is 100 mbps, so will I really notice a difference?

Once last question (i promise :) ) is that, will there be any trouble if I use two seperate distros (for example Ubuntu and Gentoo).  I'm guessing so, but does anyone have any thoughts on this?

Thanks in advance

Rick

---

### Post by RicJD on 2005-07-20
Hey, does anyone have any ideas on this, or is it just a stupidly stupid idea?

---

### Post by kdepa on 2005-07-20
This should be possible - similar things are done with Mac OS X and Windows XP when they're under a form of directory services.  I can't see any reason why Ubuntu wouldn't be able to.

---

### Post by gruepig on 2005-07-20
Not stupid at all.  If all your systems are running Linux/Unix, take a look at NFS.  It's designed to do exactly what you're asking.  For sharing with Windows (and Linux), use samba.

---

### Post by crashtest on 2005-07-20
[QUOTE=RicJD]Hey, does anyone have any ideas on this, or is it just a stupidly stupid idea?[/QUOTE]

It's totally standard in corporate networks.  As someone else mentioned, look into NFS (Network File System)

---

