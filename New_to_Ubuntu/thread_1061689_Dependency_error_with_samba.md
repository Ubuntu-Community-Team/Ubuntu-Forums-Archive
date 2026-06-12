---
title: "Dependency error with samba"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by longtom on 2009-02-06
I think I have a problem with my samba in general. When I type:

**sudo apt-get install samba smbfs**

This is what I get:

[b]Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
samba: Depends: samba-common (= 2:3.2.3-1ubuntu3) but 2:3.2.3-1ubuntu3.4 is to be installed
smbfs: Depends: samba-common (= 2:3.2.3-1ubuntu3) but 2:3.2.3-1ubuntu3.4 is to be installed
E: Broken packages[/b]

I reckon if get that fixed I might be a step closer to get some network printers on my WinXP network going.

Anybody knows how to fix above error? Any tips will be gratefully received.

longtom

---

### Post by longtom on 2009-02-06
bump

---

