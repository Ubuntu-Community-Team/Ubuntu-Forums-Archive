---
title: "Can't install recommended updates?"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Fraoch on 2010-05-06
Today language-pack-gnome-en appeared on the "Recommended Updates" section of the Update Manager window - but it's greyed out and can't be selected to install.

Shell commands like apt-get update also indicate there's 1 package not installed.  Synaptic indicates:

```
language-pack-gnome-en:
  Depends: language-pack-gnome-en-base (>=1:10.04+20100422) but 1:10.04+20100421 is to be installed
  Depends: language-pack-en-base (>=1:10.04+20100422) but 1:10.04+20100421 is to be installed
```

Huh?

Any ideas?  Should I force-install?

---

### Post by philinux on 2010-05-06
Try this

```
sudo dpkg --configure -a
```

---

### Post by Fraoch on 2010-05-06
Thanks but that didn't seem to do anything - the update is still sitting greyed out in "Recommended Updates".

---

### Post by jimmyjones on 2010-05-06
> **Fraoch said:**
> Thanks but that didn't seem to do anything - the update is still sitting greyed out in "Recommended Updates".

Same issue, same result. It looked like some updates went through today, tehn when it checked again I got the grayed out Update Manager

Got this when I went through the terminal


ffrfrf@jrff:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory

---

### Post by ranch hand on 2010-05-06
Why not go over to synaptic and get some real information?

Might be worth a try.

---

### Post by jimmyjones on 2010-05-06
> **ranch hand said:**
> Why not go over to synaptic and get some real information?

Might be worth a try.

Thanks, that worked

They were listed as upgradeable, upstream, but missing dependencies, I marked for complete removal.

All fixed (I think, hope)

---

### Post by Fraoch on 2010-05-06
> **ranch hand said:**
> Why not go over to synaptic and get some real information?

Might be worth a try.

I did check it and put it in the first post.  It indicated:

```
language-pack-gnome-en:
  Depends: language-pack-gnome-en-base (>=1:10.04+20100422) but 1:10.04+20100421 is to be installed
  Depends: language-pack-en-base (>=1:10.04+20100422) but 1:10.04+20100421 is to be installed
```

As for removing it like jimmyjones did, uhh...won't I need it?

---

### Post by ranch hand on 2010-05-06
If you run a search on the package it wants you may be able to find it, or just wait for it to become available.

I do not think I have ever removed that particular package myself.  I generally remove or avoid installing all of the buggers but I do try to use English as it is the only one I have any real knowledge of.

Removing it or even purging it and reinstalling it may work but I would just wait for the correct package to show up.

I would use apt or synaptic until it does.  Personally, I never use Update Mangler.  I have it disabled on all my installations, can't stand it.

---

### Post by Fraoch on 2010-05-07
Well - it looked like just a little boo-boo over the update servers, today there was a new version which Update Manager did not recognize as a regression but as an upgrade.  It installed it and it's gone from the list.  Back to normal.

---

