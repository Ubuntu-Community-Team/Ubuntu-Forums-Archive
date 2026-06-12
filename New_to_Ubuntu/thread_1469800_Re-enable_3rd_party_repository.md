---
title: "Re-enable 3rd party repository"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Wheel on 2010-05-02
Hi everyone,

I've just upgraded (via Update Manager) from Karmic to Lucid.  So far, I like what I see.

During the upgrade, my only third party repository (Dropbox) was disabled.  I realize that this is routine during an upgrade, although this is my first experience upgrading Ubuntu.

In Software Sources--Other Software tab, the 3 relevant Dropbox entries are prepended with "disabled on upgrade to lucid" and the boxes are all unchecked.

I have re-checked those boxes, then--in the next dialog box/window--I have clicked "Reload".

Is this enough to actually re-enable these?

Is there something else that I need to do to to ensure that I get Dropbox's updates when they become available using Update Manager?

---

### Post by zvacet on 2010-05-02
> Is this enough to actually re-enable these?

Yes it is.You can check if that repos are enabled in your source list by typin in terminal

```
gksudo gedit /etc/apt/sources.list
```

and be sure that there is no # sign in front of that repos.If you see # sign in front of that repos remove that sign.Close and save file.

```
sudo apt-get update
```

---

### Post by ddecator on 2010-05-03
Another option is going to System > Administration > Software Sources, Other Software, then checking the boxes next to the PPAs you want to have enabled.

---

### Post by Wheel on 2010-05-03
Thanks for your responses.  I'm marking this as solved.

---

