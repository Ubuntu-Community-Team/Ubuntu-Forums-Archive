---
title: "Rhythmbox 0.13.1"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by snip3r8 on 2010-09-21
I want to install rhythmbox 0.13.1 on karmic (update from 0.12.5)
,i downloaded a .deb package but it has many dependencies ,how can i do it through apt?

---

### Post by bradleypariah on 2010-09-21
That's the same version available through the repositories.
Why don't you just use the Ubuntu Software Center to install it?  It will install all of the dependencies automatically.

---

### Post by snip3r8 on 2010-09-21
i can only upgrade through synaptic as far as 0.12.8,do you know of a repository that has 0.13.1 or 0.13.0?

---

### Post by Joe of loath on 2010-09-21
What version of Ubuntu are you running?

---

### Post by snip3r8 on 2010-09-21
karmic

---

### Post by NightwishFan on 2010-09-21
Unless you find a ppa or compile it yourself, you should stick to the older version of Rhythmbox. Installing a new one will break too many dependencies on older software.

---

### Post by Dustin2128 on 2010-09-21
> **snip3r8 said:**
> karmic
I'm thinking the software packages won't be updated after a point, and karmic isn't an LTS release. You could just list the dependencies and apt get them, e.g.
apt-get dependency1 dependency2 dependency3 etc.
you just need to have a space between each of them. Unless of course, the dependencies need upgraded versions. If that's the case, it might be less of a hassle just upgrading to lucid.

---

### Post by david.rahrer on 2010-11-27
Except Lucid only has 0.12.8 available as well.  I'm tring to find a way to upgrade to 0.13.x as well because 0.12.8 has a number of bugs.  I'm on Lucid which I hope will be updated as a LTS release, but Maverick recently got 0.13.2.  Building from source presents too many problems as it appears some basic interoperability changes were made. It's frustrating.

---

### Post by brianC on 2010-12-10
Installed .13 

[http://www.webupd8.org/2010/06/install-rhythmbox-from-ubuntu-1010.html](http://www.webupd8.org/2010/06/install-rhythmbox-from-ubuntu-1010.html)

---

### Post by david.rahrer on 2010-12-11
> **brianC said:**
> Installed .13 

[http://www.webupd8.org/2010/06/install-rhythmbox-from-ubuntu-1010.html](http://www.webupd8.org/2010/06/install-rhythmbox-from-ubuntu-1010.html)

I tried that (it's now at .13.1) but the app indicator part is messed up and the UbuntuOne plugin (which is a faked version of 1.9x) doesn't work and caused errors.  The bugs in Rhythmbox were corrected, however.  

It's really quite frustrating.  This is a fairly major application in a LTS release, and I can't really find any official mention of work on a backport to solve these issues.  The current version of the application works fine, just adapt it for Lucid and get it out.

---

