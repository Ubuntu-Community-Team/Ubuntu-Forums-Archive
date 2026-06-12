---
title: "Running script at startup"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by NuttyMonk on 2009-02-10
Hi all,

I wrote a script recently and added it somewhere so it would run at startup.  Now i can't remember where i put that command which runs it at startup.

I checked "System -> Preferences -> Sessions" but i can't find it in there, yet it is still running at startup and i want to stop it running for a wee while so i can check something.

Any ideas where i might have put the command which runs it?  The Linux filesystem is still very confusing for me  :-)

Cheers

NM

---

### Post by glennric on 2009-02-10
We may need a little more information.  How do you know the script is still running?  Do you know the name of the script?

---

### Post by NuttyMonk on 2009-02-11
it was a script to mount drives at startup and they're sill being mounted.

Are there any files which i could have put the scripts name and location into which will run the script at startup?

---

### Post by adult swim on 2009-02-11
did you edit your fstab?
/etc/fstab

---

### Post by NuttyMonk on 2009-02-11
damn, you're right.  i didn't check there.

i was having problems getting the drives mounted using fstab so i created a script to do it.  it seems i must have gotten fstab working after all and must have removed the script from the "Sessions" startup tasks.

Thanks guys.

Appreciate your help.

:-)

---

