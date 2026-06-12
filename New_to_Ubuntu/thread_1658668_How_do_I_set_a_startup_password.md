---
title: "How do I set a startup password?"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by veryannoyed on 2011-01-02
I have resisted having websites remember my usernames and passwords because I am using am ultra-portable netbook that I wouldn't want to accidentally lose and then give the finder/thief access to everything. But I am sick of entering my passwords constantly, so I'd rather just have a startup password so if someone gets hold of my netbook, they can't log in and see my web browsing history. So, in short:

How can I have Ubuntu prompt me to enter a password upon loading? Thanks!!

---

### Post by Hoopz on 2011-01-02
Not sure about ubuntu but you could always set a password in the BIOS to prevent the computer from even booting in the first place.

---

### Post by veryannoyed on 2011-01-02
> **Hoopz said:**
> Not sure about ubuntu but you could always set a password in the BIOS to prevent the computer from even booting in the first place.
Well I had envisioned something like the Windows login screen... but a BIOS password works too. I just set it. Works perfectly (especially since Ubuntu's loading time is so short, it doesn't matter at which point the password is asked for). Thanks for the suggestion.

---

### Post by marrabld on 2011-01-03
Ubuntu asks for a password to log in by default.   did you not set a password when you installed it.

Any way do this

System --> Administration --> Users and Groups --> Password --> Change

Make sure "don't ask for password at log in" isn't ticked.

log out and log back in again.

---

### Post by veryannoyed on 2011-01-03
> **marrabld said:**
> Ubuntu asks for a password to log in by default.   did you not set a password when you installed it.

Any way do this

System --> Administration --> Users and Groups --> Password --> Change

Make sure "don't ask for password at log in" isn't ticked.

log out and log back in again.
Thanks. That was the first place I looked to set a password and I couldn't. Maybe I have a different version or I'm looking somewhere wrong, because there's no such options. I do have "set password by hand," which I did, but that didn't do anything. I have version 8.04. The BIOS password will do.

---

### Post by marrabld on 2011-01-05
In a terminal try typing 

```
passwd
```

And follow the prompts.  That will make sure there is a password.  As far as making you type it when you log in, it must be somewhere in the GUI or perhaps in 

```
gconf-editor
```

---

