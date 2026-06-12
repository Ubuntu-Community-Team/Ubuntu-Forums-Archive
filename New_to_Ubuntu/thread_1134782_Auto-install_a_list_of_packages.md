---
title: "Auto-install a list of packages"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by ugly_peter on 2009-04-23
Is it possible to configure Ubuntu to automatically install a list of packages in addition to the default ones? I format pretty often, so remembering and reinstalling all the packages is sort of a pain. For example: vim, subversion, git etc ...

What is the general approach to automating a modified install?

---

### Post by Hospadar on 2009-04-23
I would just save a list of all the packages you want in a text file somewhere, and when you get to a new installation, just copy and paste into an apt-get command, for example:

sudo apt-get install vim subversion git etc someotherpackage whatever

I think there may be more "advanced" ways of doing this, but it seems like a simple list is easiest

---

### Post by Paqman on 2009-04-23
Well, if you're going to clone another install then you can [create a list of the installed packages]("http://ubuntuforums.org/showthread.php?t=261366"), and automatically install them.

The other way to do is to just copy the names of the packages you like into a terminal command. The package manager can install as many packages as you like in one command. For example:
```

sudo apt-get install package1 package2 package3

```

I have a little text file tucked away of packages that I like to install on a fresh machine. One copy-paste and I can go have a cup of coffee while it sets it all up for me.

---

### Post by drs305 on 2009-04-23
You can have Synaptic make a list for you: File, Save Markings. You can then import it to your new install.

---

