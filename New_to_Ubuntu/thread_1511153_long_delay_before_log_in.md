---
title: "long delay before log in"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by gatorbrit on 2010-06-16
I am running a new install of 10.04 on my machine.  I did a clean install yesterday.   10.04 has run fine on this machine in the past.  No problems.   

When I boot up, it takes maybe 5 minutes before I can put in my password.   The mouse won't move and the computer appears frozen.  Then it unfreezes and all is well.

What can I do to figure out what is causing the computer to hang on  start up?


Thanks

---

### Post by zkriesse on 2010-06-16
Can you post your pc specs please? Might provide some insight as to what's going on that way

---

### Post by anglican on 2010-06-17
> **gatorbrit said:**
> I am running a new install of 10.04 on my machine.  I did a clean install yesterday.   10.04 has run fine on this machine in the past.  No problems.   

When I boot up, it takes maybe 5 minutes before I can put in my password.   The mouse won't move and the computer appears frozen.  Then it unfreezes and all is well.

What can I do to figure out what is causing the computer to hang on  start up?


Thanks
Try installing "bootchart" from the repos. This will show you what is taking up all the time.

H

---

### Post by gatorbrit on 2010-06-17
Thanks for the suggestions.   I am actually doing a full reinstall as I was concerned that maybe I had installed off a corrupted CD.  But the install is hanging at "update-grub"   Hopefully it will get done soon, although it has been going for an hour or so now.

---

### Post by philinux on 2010-06-17
It might be the floppy problem.

See the General Help forum Sticky.

---

### Post by ankit singh on 2010-06-17
Disable floppy in bios if u have none

---

### Post by gatorbrit on 2010-06-17
> **ankit singh said:**
> Disable floppy in bios if u have none

OK will try that.   It is still doing a fresh install.  We're at 98% now, but its taking a loooonnnngggg time.

---

### Post by DCGStudios on 2010-06-17
> **gatorbrit said:**
> OK will try that.   It is still doing a fresh install.  We're at 98% now, but its taking a loooonnnngggg time.

Yea most people have disabled floppy in bios and had instant success, for me I run a macbook pro and have no access to EFI so that wasn't an option for me. But when I did a fresh install it was fixed, so upgrades may also be a cause of the bug.

---

### Post by gatorbrit on 2010-06-17
> **DCGStudios said:**
> Yea most people have disabled floppy in bios and had instant success, for me I run a macbook pro and have no access to EFI so that wasn't an option for me. But when I did a fresh install it was fixed, so upgrades may also be a cause of the bug.

That looks like it solved the problem - we're back to super speedy boot ups!!!  

Thanks very much for the simple solution:guitar:

---

