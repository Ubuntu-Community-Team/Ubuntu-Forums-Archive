---
title: "Can I just reinstall Ubuntu?"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by twentyseven on 2009-09-10
I'm new to Linux, however we use it at my office and I bug my IT guys everyday with more questions.  I am learning, and the more I learn, the more I realize I don't know crap!  I think while learning I have made some system wide configurations that may be affecting my OS.  For instance, I cannot save my display configuration for dual monitors.  I have to go through the System>Preferences>Display everytime and reconfigure it to two screens.  Can I just reload Ubuntu and remove old kernels and such and start over?  Would it be smart to set up a second user for myself so I don't screw things up as a root user?

Thanks.  Sorry for length.

---

### Post by llamabr on 2009-09-10
no reason not to.  

and yes, a second user often comes in handy, when you're not sure if you've ruined some local config

---

### Post by mediax on 2009-09-11
The best bit of advice I'm come across with regard to fresh installations is to set up a separate /home partition.  This means that your data files, etc don't get overwritten by the new install (although, of course, you shouldn't rely solely on that to preserve important data!)

If you search the forums you'll find some good howtos on what's involved.

With regard to the second user issue, I've always found that having to run sudo commands is enough to stop me doing something as root without realsing it.

---

### Post by philinux on 2009-09-11
> **twentyseven said:**
> I'm new to Linux, however we use it at my office and I bug my IT guys everyday with more questions.  I am learning, and the more I learn, the more I realize I don't know crap!  I think while learning I have made some system wide configurations that may be affecting my OS.  For instance, I cannot save my display configuration for dual monitors.  I have to go through the System>Preferences>Display everytime and reconfigure it to two screens.  Can I just reload Ubuntu and remove old kernels and such and start over?  Would it be smart to set up a second user for myself so I don't screw things up as a root user?

Thanks.  Sorry for length.

If you screw things up as the root user then all other users will be affected if it is a system wide change that goes wrong.

---

### Post by twentyseven on 2009-09-14
Thanks Everyone.  I haven't really installed anything on my system as far programs go.  At least nothing I can't install again.  I think I'll just re-install and start over.  I keep my important data on a 1 TB external hard drive and on my primary drive (500 GB).

Thanks again.  I'm sure I'll another question soon.

---

### Post by blackened on 2009-09-14
The need for a total reinstall to solve a problem is a holdover from the Windows world. Rarely will you come across something so bad as to necessitate going to those lengths.

Unfortunately display settings is one of those areas where the OS is still really flaky. The best solution I can suggest would be to use a bash script to enable your proper display settings at login.

If you'll post the output of 

```
xrandr --prop
```

we'll see what we can come up with.

---

### Post by steveneddy on 2009-09-14
It really doesn't hurt to reinstall if the system is borked.

It may be faster than trying to figure out the issue.

Just reinstall and start over, noting where you made mistakes last time and try not to make the same mistakes twice.

Even research scientists make notes of failures and start over and then view the results, good or bad, until they come to an acceptable conclusion.

---

