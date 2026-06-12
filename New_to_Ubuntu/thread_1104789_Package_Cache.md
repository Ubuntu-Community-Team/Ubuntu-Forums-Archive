---
title: "Package Cache"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Bri0 on 2009-03-24
Is there a limit in the package cache ( /var/cache/apt/archives )? Because I had 420MB of packages that I backed up today using APTonCD and now the cache location is down to 220MB.

I do have the Synaptic setting to leave all packs in its cache.


What's up with this?  Thanks

---

### Post by cariboo on 2009-03-24
Apt will store as many packages as you have room for on your hardrive. By default aptoncd does don't store older duplicate packages in the iso, so it could be that that size of the iso is different because of the older duplicate packages.

As you can see from my screenshot I have 770Mb of packages in the archive, but the iso will only be 560Mb

Jim

---

### Post by Bri0 on 2009-03-24
I have room, and I am aware that APTonCD doesn't include older packs, but it shouldn't have gone down that much.

It actually removed packs that where current. It did it after the backup with APTonCD. I ended up clearing the cache and using the APTonCD to restore all the packs back.

---

### Post by longtom on 2009-03-25
I don't trust APTonCD.  I know - people swear by it, but I had bad experiences and it turned on me.  Maybe something I did wrong - so I can't imgine what you can do wrong with APTonCD.

What I do and what really works for me - and a lot of offline PCs I "service":

Make a straight copy of the cache and create a harddrive repository and install from there.  So all the packs are included which are in the cache.

Still missing dependencies sometimes...but that appears "par for the course" for the offline user.  Otherwise I find this a reliable back-up method.

---

### Post by KIAaze on 2009-03-25
If you don't mind downloading packages again (and don't have 700MB of cache/CD to waste), this might interest you:
[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)
(also has instructions for rpm-based distros)

The GUI way to do it:
[http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html](http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html)

Backup/restore PEAR packages:
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

Another one while I was trying to find the first link again:
[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

---

