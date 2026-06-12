---
title: "I have wicd from tar.gz, how to switch to deb pack?"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by stozi on 2009-07-27
Please don't ask why I have wicd installed from a tar.gz, it's not something I'm proud of. I am not skilled enough to do much manually. I know my wifi chip is Ralink, and I know wicd makes it work automatically, and that's about it. I tried installing wicd from synaptic and then uninstalling the tar.gz one, but this didn't work. I know network-manager and wicd conflict, but I think if I quit wicd right after synaptic downloads network-manager it may be ok. I can then switch from network manager to wicd easily. 

Will it work? Any better ideas?

---

### Post by bodhi.zazen on 2009-07-28
Use the .deb

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Depending on what version of Ubuntu you are using, simply enable the "universe" repository and ```
sudo apt-get install wicd
```

---

### Post by stozi on 2009-07-28
Thanks, so when I got wicd from synaptic before I immediately uninstalled the version from the tar.gz by terminaling "python setup.py uninstall. After rebooting wicd didn't work for me. This time, I just installed from synaptic and moved the tar.gz install to the trash. Is there anything bad that could come of doing it like that?

---

### Post by The Cog on 2009-07-28
I don't think there should be a problem. Your .deb install should create all the files it wants, overwriting the other install if necessary. It is possible that there may be some files left over from the tar.gz, but even if there are, they shouldn't cause a problem.

I really don't understand why wicd isn't the default network manager. It works so much better.

---

