---
title: "[SOLVED] Need help with chown on Ubuntu 8.10"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by gkschermer on 2009-01-03
Last night I wasn't thinking at all (thanks to a bottle of wine) and I thought that I would change the ownership of everything in my home folder to my user (I have transferred a lot of files from my old computer).  Anyway, in my drunken state I typed the following:

```
sudo chown -R gavin /.

```

Things still seemed to work until I rebooted this morning and now nothing is working right.  I have tried to chown everything back to root but that hasn't helped either.  

Is there a simple fix to this or do I need to reinstall?

---

### Post by scragar on 2009-01-03
You have just chowned the entire root file system, that's not good, and I'm not sure there's a good fix, since a lot of things will belong to other users, not just you or root(syslog has it's own user, as does gdm, etc...)


(If you have a liveCD or alternate install CD, you might be able to restore the installed systems defaults with minimal downloading, just pop in the CD, and start the package manager when prompted, now click installed in the status tab, and then use ctrl+A to highlight everything, and mark them for reinstall, it will take a while to complete, but I think it's the safest method of restoring the settings)

---

### Post by BDNiner on 2009-01-03
wow, the main issues i see are that you did not specify a group and i don't know what directory /. would be. your home direcory is ~/yourusername. If the command happened to make you the owner of everything on the disk with no group specified then I would reinstall. It maybe too much work to undo everything. That is just my opinion on the matter.

---

### Post by nemilar on 2009-01-03
I second... just re-install.

---

### Post by Copernicus1234 on 2009-01-03
Almost as bad as sudo rm -rf /. :)

I think you should reinstall. It doesnt take that long and you make sure you dont get strange errors because of this in the future. Like others have said, you just changed the owner of all files and folders on the hard drive to be you instead of root.

---

### Post by gkschermer on 2009-01-03
Thanks all.

I guess this just goes to show that chown and a bottle of wine do not mix.

---

