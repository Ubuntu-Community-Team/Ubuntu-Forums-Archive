---
title: "Gyachi"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by gatoguts on 2009-05-10
I download Gyachi using the link below provided in one of the forums here:

[https://launchpad.net/%7Eloell/+arch...ntu11_i386.deb](https://launchpad.net/%7Eloell/+arch...ntu11_i386.deb)

Ho do i completely remove this program?

---

### Post by albinootje on 2009-05-10
> **gatoguts said:**
>  Ho do i completely remove this program?

Please post the output of the following :
```

dpkg -l|grep -i gyachi

```

---

### Post by AndThenWhat on 2009-05-10
Open Synaptic by going to System -> Administration -> Synaptic Package Manager.

From there on the left click "Installed (local or obsolete)."  Then right-click on gyachi in the list and select "Mark for Complete Removal."  Now, press Apply and after it finishes Gyachi should be completely removed.

---

### Post by gatoguts on 2009-05-10
> **AndThenWhat said:**
> Open Synaptic by going to System -> Administration -> Synaptic Package Manager.

From there on the left click "Installed (local or obsolete)."  Then right-click on gyachi in the list and select "Mark for Complete Removal."  Now, press Apply and after it finishes Gyachi should be completely removed.

unfortunately it is not showing as installed in synaptic...what i really want to do is reinstall gyachi by adding the repositories and PPA keys...that link used GDebi package installer..i wanted to redo it with the necessary authentication

---

