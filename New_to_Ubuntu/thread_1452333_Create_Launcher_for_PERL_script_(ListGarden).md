---
title: "Create Launcher for PERL script (ListGarden)"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by RemiemB on 2010-04-11
I'm having a hard time! I'm using ListGarden (written in PERL) to create RSS Feeds for my site. I want to create a desktop launcher for that app. How do I do that? Help!

---

### Post by Didius Falco on 2010-04-11
Have a look at this:

[http://calypso.tux.org/pipermail/novalug/2007-June/090076.html](http://calypso.tux.org/pipermail/novalug/2007-June/090076.html)

I hope it helps you out.

Regards,

Didius

---

### Post by RemiemB on 2010-04-11
Tried it. Terminal opens briefly, then closes. It's driving me nuts!

---

### Post by kthakore on 2010-05-19
Try PAR::Packer

```
cpan Module::ScanDeps PAR PAR::Packer

pp -o listgarden.run listgarden.pl

./listgardern.run 
```

If you get errors for missing modules add them with -M tag.

Also see

```
perldoc pp
```

---

