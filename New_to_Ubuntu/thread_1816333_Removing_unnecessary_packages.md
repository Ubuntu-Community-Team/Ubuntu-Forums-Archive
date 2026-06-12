---
title: "Removing unnecessary packages"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by roodypoo on 2011-08-01
Is there a way to see when the last time a package was used? I want to remove everything that isn't necessary from my system. For example My desktop doesn't have bluetooth but the capability installs with the standard installation. If I've never used it, the date last accessed should be when I installed the system.

Thanks

---

### Post by Rex Bouwense on 2011-08-01
I cannot answer you question but would like to submit a caution.  Some of these installed programs are inter-twined, so uninstalling one could possibly cause another to screw up.  Knowing or suspecting that and realizing that I have a very large hard drive, I opted to just insure that the programs that I did not use did not start at boot.  Why not.  They don't take up a lot of room.  I will be interested in the responses that you get.

---

### Post by mikewhatever on 2011-08-01
A system wouldn't really use installation packages for anything other then installing. It would use the installed files, and so, following your idea, one would need to check all files in /, about a hundred thousand of them.
Instead of going this tedious and time consuming rout, start with Ubuntu minimal, and add packages you think you need.

---

### Post by Paqman on 2011-08-01
[Popcon]("http://packages.ubuntu.com/natty/popularity-contest") actually does track how often various things are used. You should be able to get it to spit out a list of the most unused packages with:
```

popularity-contest | grep '<OLD>'

```
I'm not sure if popcon is in the default install any more though, you may need to install it and then come back to it in a while.

---

### Post by roodypoo on 2011-08-01
> **Paqman said:**
> [Popcon]("http://packages.ubuntu.com/natty/popularity-contest") actually does track how often various things are used. You should be able to get it to spit out a list of the most unused packages with:
```

popularity-contest | grep '<OLD>'

```I'm not sure if popcon is in the default install any more though, you may need to install it and then come back to it in a while.

```
c@c:~$ popularity-contest | grep '<OLD>'
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
readline() on closed filehandle FILES at /usr/sbin/popularity-contest line 104.
c@c:~$ 

```

Any ideas on that?

Also, Ubuntu minimal sounds cool. I'm going to check that out.

If a two packages require a certain dependency, removing one will also remove the dependency for the other?

---

### Post by Paqman on 2011-08-01
> **roodypoo said:**
> 
Also, Ubuntu minimal sounds cool. I'm going to check that out.


Check out the script in my sig. You can use it to create a nice basic system that works, then add packages from there.

> 
If a two packages require a certain dependency, removing one will also remove the dependency for the other?

No, removing a package doesn't remove the packages that it depends on (although you can make it do that if you want).

---

### Post by pmooney78 on 2011-08-01
Another thought: Occasionally, run ```
sudo apt-get autoremove
``` from a terminal. It will remove any packages that were automatically installed to satisfy a dependency, but aren't currently needed by other packages.

---

### Post by wildmanne39 on 2011-08-01
Hi, +1 for a Minimal Install.

---

### Post by EkuquoL on 2011-08-01
.... Computer Janitor...

Available via Ubuntu's  Software Center / Package-manager : Synaptic

Computer Janitor by GNU - analyzes packages(That are not in use) on your system and can remove them safely.
For Gnome / Unity 

I believe there is a KDE Kcleanup or something like that for the KDE4 environment. 

..Bleachbit .. 

Another, neat temp file cleaner is bleachbit--can be programmed as well--cleans temp files throughout your system. Just run it as root to get the entire functionality out of it.
Bleachbit is available at Ubuntu's repository / Package manager

---

