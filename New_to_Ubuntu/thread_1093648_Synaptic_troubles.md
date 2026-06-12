---
title: "Synaptic troubles"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Periswell on 2009-03-11
hello 
when ever i enter synaptic it keeps on coming up with the error:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
so i go into the terminal and put it in and this is what i get:
> joshua@joshua-laptop:~$ sudo dpkg --configure -a
[sudo] password for joshua: 
dpkg: parse error, in file `/var/lib/dpkg/updates/0125' near line 1:
 MSDOS EOF (^Z) in field name `.gz'
joshua@joshua-laptop:~$ 
what do i do at this point? Thanks in advance.

-joshua

---

### Post by carml on 2009-03-11
Try to go to System->Administration->Synaptic Package manager to get a updated list of packages, I'm used to work with the gui rather than the terminal.
It should resolve the problem :).

---

### Post by Periswell on 2009-03-13
i cant, everytime i go into the gui version of synaptic it comes up with that message and the only button is close, no ok so i cant do anything with it. i cant install stuff with terminal or update. i cant even run sudo apt-get update without the message popping up.

-joshua

---

### Post by avtolle on 2009-03-13
It looks like a corrupted file from the error message. It seems to me you would need to remove or purge the file from /var/lib/dpkg/updates then try again. Sorry, don't have the precise syntax for the  command at my fingertips right now; I'm at work and my notes are at home.

---

