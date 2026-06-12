---
title: "problem with dpkg after running out of hd space"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by SydneyGB on 2009-10-19
I tried to install kubuntu-desktop, not realising I was nearly out of HD space.  apt failed to write a bunch of things, naturally, and now I can't run apt or synaptic.

The system told me to run dpkg --configure -a, which I did.  It gave me this: 

dpkg: parse error, in file `/var/lib/dpkg/updates/0178' near line 1:
 newline in field name `#padding'

I opened that file in nano and there are a stack of #padding  lines there, but I've no clue what I ought to do to fix the problem.  I can't see any markups (presuming 'newline' means a symbol that creates a new line in the text).

Can anyone help me out?

---

### Post by LewRockwell on 2009-10-19
rescue/recover your valuables and then repartition as desired...then a fresh install...

.

---

### Post by Eclipse. on 2009-10-19
sudo apt-get clean
sudo apt-get autoclean

That will clear your computer of files you dont need.

---

### Post by SydneyGB on 2009-10-20
> **Eclipse. said:**
> sudo apt-get clean
sudo apt-get autoclean

That will clear your computer of files you dont need.

I ran clean without a hitch, but autoclean produces the same error I listed above.  I don't know if it makes a difference, but this is a Wubi install.  Is it possible to delete the offending file, or will that make things worse?

---

### Post by SydneyGB on 2010-01-01
Any further advice on this problem, folks?  I'm prepared to reinstall if it comes to that, but I'd like to know if there are any options less catastrophic that I've missed.

Thanks for the help you've given thus far. :)

---

