---
title: "Should &quot;Hal&quot; still be installed in Karmic?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-10-30
Hey everyone,

I've been having some issues with udev, the new hardware manager designed to replace hal in Ubuntu 9.10

However, in synaptic package manager, hal is still checked as "installed". Should I remove it?

---

### Post by Mark76 on 2009-10-30
Xserver still relies on it (for now). Best to wait until it's officially removed.

---

### Post by kansasnoob on 2009-10-30
Yes, it should be installed! Deprecation is not complete.

Do not remove it!

I hope that edit made it in time! I'd just said yes without reading your entire thread, I can be a dumb-*** sometimes like that!

---

### Post by asuastrophysics on 2009-11-03
> **kansasnoob said:**
> Yes, it should be installed! Deprecation is not complete.

Do not remove it!

I hope that edit made it in time! I'd just said yes without reading your entire thread, I can be a dumb-*** sometimes like that!

It's okay, I understood what you were saying. Thanks! :mrgreen:

Thread -> Solved

---

### Post by tpost001 on 2010-02-24
What I would like to know is...

Should hal and udev be activated (checked) in the Boot-up Manager?  Both services are not activated on my 9.10 Dell XPS M1210 laptop.

---

### Post by asuastrophysics on 2010-02-25
> **tpost001 said:**
> What I would like to know is...

Should hal and udev be activated (checked) in the Boot-up Manager?  Both services are not activated on my 9.10 Dell XPS M1210 laptop.

does everything seem to work okay? 

if so I wouldn't personally mess with it, especially since the developers have this half udev, half hal frankenstein monster thing going on ;)

i, personally have found that the boot-up manager contains a hell of a lot of old packages that have just been unchecked due to upgrading from previous versions. i just either leave them alone or delete them from the list to get rid of the temptation to mess things :P

---

### Post by tpost001 on 2010-02-26
Thanks for that comment.  Yep, everything seems to work okay.  Actually 9.10 is my best experience yet with Ubuntu.  You are right.  I have an awful lot of unchecked services in there, many of which are checked in 8.04 or 9.04 (I skipped 8.10).  I'll leave them alone and hope this will be cleaned up for 10.04.

---

