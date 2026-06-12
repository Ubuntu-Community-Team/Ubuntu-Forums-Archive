---
title: "Cannot copy a file to /usr/lib/nx wrong permissions"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Notac on 2010-09-08
I am trying to install FreeNX and all was going well, following the documentation from this site.
Ithen states to download a setup file which no longer gets pulled down with the packages.
I can download the nxsetup file but I am unable to extract or copy it to the appropriate folder to carry on with the installation.

I have made myself an Administrator (Manage users and groups) but this made no difference.

Any and all help on this matter will be appreciated

---

### Post by sandyd on 2010-09-08
> **Notac said:**
> I am trying to install FreeNX and all was going well, following the documentation from this site.
Ithen states to download a setup file which no longer gets pulled down with the packages.
I can download the nxsetup file but I am unable to extract or copy it to the appropriate folder to carry on with the installation.

I have made myself an Administrator (Manage users and groups) but this made no difference.

Any and all help on this matter will be appreciated
```

gksudo nautilus /usr/
```
drag n drop into the "bin" folder
Note that I did not open the bin folder directly, because that would likely cause your file browser to freeze for a while.

---

### Post by gnicko on 2010-09-08
> **Notac said:**
> 
I have made myself an Administrator (Manage users and groups) but this made no difference.

Not quite sure what you mean by this....

The deal is, in a nut-shell, the folders outside of your home directory aren't yours. They belong to the system (a.k.a. "root")

In order to put things in there, you have to either be root or have "root's permission" to do so.

How familiar are you with working from a command line? You should be able to "sudo" in there and do what you need.

---

### Post by gnicko on 2010-09-08
> **carlee said:**
> ```

gksudo nautilus /usr/
```
drag n drop into the "bin" folder
Note that I did not open the bin folder directly, because that would likely cause your file browser to freeze for a while.


Well, yeah, or that....

---

### Post by kerry_s on 2010-09-08
use the ppa, it's much easier & you'll get any new updates.
[https://launchpad.net/~freenx-team/+archive/ppa](https://launchpad.net/~freenx-team/+archive/ppa)

---

### Post by Notac on 2010-09-10
Thank you all for your replies.
Have now solved by re-installing 10.4.1LTS and getting the packages required direct from the Nomachine website.

I re-installed because I believe I had made a few errors and there were a couple of items that I had installed in error but was unsure as to how to remove them, that and it only takes 10-15 mins to do a fresh install. (Yes my Installation is that new, only started looking at Ubuntu a week ago)

Once again, thank you for your assistance :D

---

