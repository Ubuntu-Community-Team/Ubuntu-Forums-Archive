---
title: "Update Manager: How To Make Silent for Unwanted Files?"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by JamesV on 2009-01-25
I have an Nvidia video card. Update Manager keeps telling me there are two updates available for ATI and Radeon video. I assume there's no point in downloading these. I tried unchecking the files in UM but with every logon it keeps alerting me. How do I tell UM to quit bugging me about files I don't want?

Or, is there a good reason I should update these files anyway?  I'm using Intepid 8.10, kernel 2.6.27-9-generic, gnome 2.24.1.

---

### Post by sdennie on 2009-01-25
It's probably safe to remove those packages if you aren't using them.  Try removing them with:

```

sudo apt-get remove name-of-package

```

As long as it doesn't say that it's going to remove a bunch of other packages as well, it's safe to remove them.  The other option is to just upgrade them.

---

### Post by JamesV on 2009-01-25
> **sdennie said:**
> As long as it doesn't say that it's going to remove a bunch of other packages as well, it's safe to remove them.  The other option is to just upgrade them.

It said it was going to remove xserver video-all, not just the ATI. That scared me so I took your second suggestion. Thanks for the help.

---

### Post by cubeist on 2009-01-25
or you can go into synaptic and choose "force version" (it's in the menus) and this will lock a package at a particular version and won't pester you to upgrade.

---

### Post by sdennie on 2009-01-25
> **JamesV said:**
> It said it was going to remove xserver video-all, not just the ATI. That scared me so I took your second suggestion. Thanks for the help.

It would have been safe to remove xserver-xorg-video-all.  It's just a meta package that points at all the possible video drivers.  If you know you are using a certain driver, removing that meta package shouldn't have any adverse effects.  Though, if you upgrade to a new version of Ubuntu, it might not bring in all the xorg drivers.

---

### Post by drugon on 2009-01-25
UM is working on the links of the sources provided. so type 
$ sudo gedit /etc/apt/sources.list

once this file opens, go through all the links in the file and if you find one with the descriptions of ATI and Radeon, just put "#" (Hash) in front of the link to deactivate that. 

the reason for deactivating them rather than deleting is, incase if you need that in future or if it is not the right link then you have the backup.

Hope this helps.

---

