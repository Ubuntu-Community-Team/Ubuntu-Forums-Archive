---
title: "update manager and third party software sources"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by mashedbear on 2009-07-04
Since upgrading to ubuntu 9.04 i noticed there was a 'grayed' out update showing in the update manager interface which I can't select to update gstreamer0.1-plugins-bad. 

What do I need to change to be able to update this in 9.04?

Also I seemed to have a number of Akirad Repositories listed in the third party sources interface which are all disabled. What are these?

Thanks for any help

---

### Post by scrooge_74 on 2009-07-05
Can you use synaptic to view the packages?

---

### Post by CatKiller on 2009-07-06
> **mashedbear said:**
> What do I need to change to be able to update this in 9.04?

gstreamer0.10-plugins-bad is in the Universe repository. You can enable this at System -> Administration -> Software Sources.

> Also I seemed to have a number of Akirad Repositories listed in the third party sources interface which are all disabled. What are these?

They are repositories that you've previously added as software sources. Third-party sources are disabled on an upgrade because they can't be assumed to have packages for the new release. If you still want them to be used you'll need to find out if there is a repository for the release you are now using and amend them accordingly.

---

### Post by mashedbear on 2009-07-06
> **CatKiller said:**
> gstreamer0.10-plugins-bad is in the Universe repository. You can enable this at System -> Administration -> Software Sources.



Thanks - I think universe repository is already enabled in software sources. Can I check this at the command line?

---

### Post by CatKiller on 2009-07-06
> **mashedbear said:**
> Thanks - I think universe repository is already enabled in software sources. Can I check this at the command line?

You can read your sources.list.

```
less /etc/apt/sources.list
```

---

