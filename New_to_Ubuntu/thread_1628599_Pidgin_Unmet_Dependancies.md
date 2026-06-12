---
title: "Pidgin Unmet Dependancies"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by fleamour on 2010-11-22
I had Pidgin installed & added Pidgin PPA Package to upgrade to latest version.  All to avoid the recent certificate issue.

But Pidgin still had a problem with the MS certificate so I uninstall-ed Pidgin & now cannot reinstall as get following error:

"Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.

pidgin: Depends: pidgin-data (<1:2.6.6-z) but 1:2.7.5-1lubuntu2+pidgin1.10.04 is to be installed

Recommends: pidgin-libnotify but it is not going to be installed"

It all sounds horribly complicated!  How can I resolve other than restore from an old image?

---

### Post by fleamour on 2010-11-24
Pretty easy, just locate the offending package listed in error message under synaptic, uninstall then reinstall Pidgin.

---

### Post by borger live on 2012-04-13
I just upgraded from 10.04 to 11.10 and have been looking for this answer.  Thanks!
:guitar:

---

### Post by raja.genupula on 2012-04-13
> **fleamour said:**
> I had Pidgin installed & added Pidgin PPA Package to upgrade to latest version.  All to avoid the recent certificate issue.

But Pidgin still had a problem with the MS certificate so I uninstall-ed Pidgin & now cannot reinstall as get following error:

"Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.

pidgin: Depends: pidgin-data (<1:2.6.6-z) but 1:2.7.5-1lubuntu2+pidgin1.10.04 is to be installed

Recommends: pidgin-libnotify but it is not going to be installed"

It all sounds horribly complicated!  How can I resolve other than restore from an old image?

yeah one more thing is you can get it by 
```
 
sudo apt-get install -f
```

it will get that pkg automatically .

---

