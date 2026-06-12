---
title: "Package Aware backup software"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by brendan-nz on 2010-06-27
Hi, 
  I've just installed ubuntu.  At the moment, 95% of my system has come from packages either installed of the CD-ROM or downloaded off the internet.  

Is there some package aware backup software that allows me to say only backup my stuff, and just has place holders for the files that came from packages?

Brendan

---

### Post by psusi on 2010-06-27
Just back up your home directory instead of the whole root filesystem.

---

### Post by brendan-nz on 2010-06-28
> **psusi said:**
> Just back up your home directory instead of the whole root filesystem.

What about the packages I have selected to install, and the changes I have made to /etc.  If I have to restore after a system failure, it'd be nice to be able to get back quickly to where I was.

---

### Post by lukeiamyourfather on 2010-06-28
Use this.

```

dpkg -l

```

That will list every package installed. Dump that to a text file with this.

```

dpkg -l > ~/packageList.txt

```

When installing on a new system copy the entire "packageList.txt" file to the clipboard and then do this.

```

sudo aptitude install ***PASTE LIST OF PACKAGES HERE***

```

Any packages already installed will be ignored, anything not part of the default install will be installed at this point. If you want use cron to schedule an automatic backup of the package list so its always up to date. Cheers!

---

