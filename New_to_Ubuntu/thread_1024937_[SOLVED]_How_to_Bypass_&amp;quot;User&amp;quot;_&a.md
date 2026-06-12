---
title: "[SOLVED] How to Bypass &amp;quot;User&amp;quot; &amp;amp; &amp;quot;Password&amp;quot;?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Hotel California on 2008-12-29
Just installed 8.04 a couple days ago.  I'm the only one who will use this computer and was wondering if I can somehow bypass the USER and PASSWORD screens so that I will end up at the desktop without any intervention after booting up.  Thanks.

---

### Post by jerome1232 on 2008-12-29
System->Administration->Login Window, Security Tab, check Automatic Login

---

### Post by Toshibawarrior on 2008-12-29
> **jerome1232 said:**
> System->Administration->Login Window, Security Tab, check Automatic Login

+1...

He beat me to it :p!

---

### Post by rrashkin on 2008-12-29
If one were to do that (automatic login), I assume the root password (for use in "sudo" or during updates) would remain unchanged.  Is that right?

---

### Post by Hotel California on 2008-12-29
That was quick and easy.  Thank you!

---

### Post by howefield on 2008-12-29
> **rrashkin said:**
> If one were to do that (automatic login), I assume the root password (for use in "sudo" or during updates) would remain unchanged.  Is that right?

Your assumption is correct.

---

### Post by ugm6hr on 2008-12-29
> **rrashkin said:**
> If one were to do that (automatic login), I assume the root password (for use in "sudo" or during updates) would remain unchanged.  Is that right?

Yes.  The "sudo" password remains unchanged for any administrators with sudo privileges.

But it is not strictly the root password (in traditional Linux terms).

---

### Post by jerome1232 on 2008-12-29
> **rrashkin said:**
> If one were to do that (automatic login), I assume the root password (for use in "sudo" or during updates) would remain unchanged.  Is that right?

correct. Also changable, but not recomended. (It's just horrible terrible security, it would give malware oportunity to destroy your system and such)

---

### Post by Hotel California on 2008-12-29
Ooops, spoke too soon.

It's bypassing the USER and PASSWORD screens, but each time it is now asking me to "Enter password for default keyring to unlock".  I enter my password and hit OK, but next bootup it does the same thing.

---

