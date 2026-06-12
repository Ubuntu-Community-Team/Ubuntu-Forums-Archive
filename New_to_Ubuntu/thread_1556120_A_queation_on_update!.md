---
title: "A queation on update!"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-08-19
HI!
We use to get an update of about 300 mb.
And everytime when we install those updates, about 500 mb space is used. So if we keep on doing this it will eat up our all memory space.
So what to do in this case?

---

### Post by dcollier on 2010-08-19
If your questions is about update eating up disk space, then I would have to say yes.  These are files download to your computer!

---

### Post by Redblade20XX on 2010-08-19
Do you download updates constantly or just on an off? If you don't update consistently, it will build up.

---

### Post by linux18 on 2010-08-19
sudo apt-get install deborphan && sudo apt-get purge $(deborphan) && sudo apt-get purge $(deborphan)
sudo apt-get install localepurge && sudo apt-get clean

---

### Post by amityadav9314 on 2010-08-19
> **Redblade20XX said:**
> Do you download updates constantly or just on an off? If you don't update consistently, it will build up.

i download the update constantly.

---

### Post by amityadav9314 on 2010-08-19
> **linux18 said:**
> sudo apt-get install deborphan && sudo apt-get purge $(deborphan) && sudo apt-get purge $(deborphan)
sudo apt-get install localepurge && sudo apt-get clean

what all these commands are for?
please explore.

---

### Post by linux18 on 2010-08-19
> **amityadav9314 said:**
> what all these commands are for?
please explore.
they will free up orphaned packages (which unnecessarily add to the update size), purge the apt caches to free up some space, and remove files that aren't in your language[s]

---

### Post by Perfect Storm on 2010-08-19
If you're worried about space, you can try Bleachbit

---

### Post by inameiname on 2010-08-19
I second Bleachbit!

---

