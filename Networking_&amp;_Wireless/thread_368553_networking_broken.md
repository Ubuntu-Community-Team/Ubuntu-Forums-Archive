---
title: "networking broken"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by robome on 2007-02-23
Hi,

I'm somewhat confused. Networking in my installation suddenly gone mad.
I noticed that when I tried to refresh the packages list in aptitude right after uninstalling some packages. Aptitude suddenly said it couldn't resolve neither de.archive.ubuntu.com nor security.ubuntu.com.

Since that point aptitude, apt-get, wget, pavuk and ssh always throw that error regardless of the address for that they're called. Interestingly Seamonkey still worked at that time--until I restarted it.
What does work is ping, host and dig as well as Konqueror and also XMMS still plays streamed stuff from the internet.

BTW, I actually can get all those applications work on an address again by inserting a specific host into /etc/hosts - but that can't be a real solution.

I'm running an up-to-date Feisty system.

What has happened before that network problem is also strange and maybe connected with it. I selected a package in aptitude but deselected it again right away after I saw the huge amount it will need.
Suddenly I got about 40 packages that will be uninstalled bcause installed by dependency and not needed anymore. Can't see why since it where so different and also essentials packages like mdetect, gs-esp-x, aspell, automake, gdb, cupsys-bsd, foomatic-db, libbonobo2-0 a.s.o.
I then indeed uninstalled all that proposed apps.

Hopefully one of you knows how to get my system work again.

Bye,
Robert

---

### Post by robome on 2007-02-23
> **robome said:**
> I'm somewhat confused. Networking in my installation suddenly gone mad.
I noticed that when I tried to refresh the packages list in aptitude right after uninstalling some packages. Aptitude suddenly said it couldn't resolve neither de.archive.ubuntu.com nor security.ubuntu.com.

Uhh, those files listed as needles were indeed connected.
The packet in question that disabled (and now reenabled) dns resolution was libnss-mdns.

But how the f*** can that happen (libnss-mdns seems not to depend on anything basic) and why does that lib (a plugin of glibc) cause dns resolution to fail?

Robert

---

### Post by koenn on 2007-02-23
well, you've diagnosed the problem : your dns is not working right, and it most likely has to do with removing mdns. 

Wild guess : the package you selected depended on a great deal of other packages, and when you deselected it, aptitude also marked for uninstall all its dependencies - iven while they were needed for other packages. This triggerd more uninstalls, etc until a packacke that mdns depends on got uninstalled, so mdns was removed as well because its dependencies were no longer satisfied. 

If you can reproduce that, it would indicate either a bug in aptitude, or an inconsistency in the dependencies. 
Long shot.

---

### Post by robome on 2007-02-24
> **koenn said:**
> Wild guess : the package you selected depended on a great deal of other packages, and when you deselected it, aptitude also marked for uninstall all its dependencies - iven while they were needed for other packages. This triggerd more uninstalls, etc until a packacke that mdns depends on got uninstalled, so mdns was removed as well because its dependencies were no longer satisfied. 

The package I selected was Anjuta which indeed triggered a great deal of Gnome stuff (mostly proposed ones). Upon unselecting what you described is possible.

The confusing part is that only very few depends on nss-mdns (?ubuntu-desktop, ichthux-desktop and kdnssd) and neither of that was previously selected though nss-mdns was installed by dependecy. But without it not few applications (as described) stop working.

> If you can reproduce that, it would indicate either a bug in aptitude, or an inconsistency in the dependencies. 
Long shot.

Will see if I can reproduce it though I fear it bears the possibility to completely mess up my system.

Robert

---

### Post by kristofer on 2007-03-08
if libnss-mdns and apt aren't playing nice you may want to check out /etc/nsswitch.conf


```
# /etc/nsswitch.conf

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

I changed the hosts line to look like this

```
# /etc/nsswitch.conf

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

now everything resolves fine.. that just makes it search the dns server from resolv.conf before checking mdns for the host.

-kb

---

