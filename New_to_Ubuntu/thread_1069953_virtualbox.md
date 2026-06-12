---
title: "virtualbox"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by chazn85 on 2009-02-14
i have a feeling this will be a really easy fix im sure.  

Basically im trying to upgrade my version from 2.0.2 to the latest but every time i try to run the new executable it obviously conflicts with the new one.  Is there an upgrade switch for dpkg?  if so i couldnt find one.

Thanks

---

### Post by geirha on 2009-02-14
How did you install the new one? .deb-file or .tar-ball or what?

Why not just uninstall the previous version? then there should be no conflict

---

### Post by frklin on 2009-02-14
Remove VirtualBox and install it from the repository ;)
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by chazn85 on 2009-02-14
main reason for not unistalling is i dont want to delete my virtualboxes.

I installed from a .deb file as the repos only has/had the OSE version when i installed it.

---

### Post by geirha on 2009-02-14
The virtual machines are stored in your homefolder, in a hidden folder called .VirtualBox. The package system never touches any of the homedirs, so uninstalling virtualbox will not uninstall your virtual machines ... only the virtualbox binaries and libraries etc.

---

### Post by chazn85 on 2009-02-14
thanks all just wanted to make doubly sure before i removed anything.

---

### Post by chazn85 on 2009-02-14
this is now solved is the solved option still availible somewhere?

---

### Post by geirha on 2009-02-14
> **chazn85 said:**
> this is now solved is the solved option still availible somewhere?

Still disabled I think. The marking as solved and thank post features were disabled because they were too heavy on the database, making the forum slugish. I'm sure they'll enable them again once they figure out a better way to do it.

---

