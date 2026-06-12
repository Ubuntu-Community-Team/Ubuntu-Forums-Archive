---
title: "Back to Ubuntu after a few years, problems with Quanta"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by bovisrex on 2010-12-31
I just loaded !0.10 on my Compaq laptop (my last Ubuntu was 7.04, but I used Red Hat for a few years before). Shortly after, I loaded Quanta Plus, but it doesn't seem to want to work completely on the default installation... among other things, it tells me that a couple of packages I've loaded... Cervisia and KImageMapEditor... aren't available, and when I pull up anything in the help menu it says that it can't load the KDE help center. Short of loading KDE on top of GNOME, which I don't want to do unless I have to, is there any way to make it fully functional? It seems like there should be since it was one of the choices available from the software center.

Thanks!

---

### Post by ikt on 2010-12-31
> **bovisrex said:**
> I just loaded !0.10 on my Compaq laptop (my last Ubuntu was 7.04, but I used Red Hat for a few years before). Shortly after, I loaded Quanta Plus, but it doesn't seem to want to work completely on the default installation... among other things, it tells me that a couple of packages I've loaded... Cervisia and KImageMapEditor... aren't available, and when I pull up anything in the help menu it says that it can't load the KDE help center. Short of loading KDE on top of GNOME, which I don't want to do unless I have to, is there any way to make it fully functional? It seems like there should be since it was one of the choices available from the software center.

Thanks!

If you go into Ubuntu Software Centre > Edit: Software Sources... > Are all 4 sources ticked?

---

### Post by bovisrex on 2010-12-31
Yup... all four choices for Ubuntu software were already checked. I checked the two Canonical options for Other Software and re-installed it... same issue.

---

### Post by ikt on 2010-12-31
> **bovisrex said:**
> Yup... all four choices for Ubuntu software were already checked. I checked the two Canonical options for Other Software and re-installed it... same issue.

Are you able to manually install those packages via synaptic?

Do you get a similar bug to this if you try installing through synaptic?

[https://bugs.launchpad.net/ubuntu/+source/kdewebdev-kde3/+bug/497200](https://bugs.launchpad.net/ubuntu/+source/kdewebdev-kde3/+bug/497200)

---

### Post by bovisrex on 2011-01-01
Both packages seemed to install just fine, but I'm still having the same issues.

I guess the other question would be: is there an HTML editor comparable to Quanta and HTML Kit that works just fine with Gnome? I'm not a big fan of NVU.

---

### Post by bovisrex on 2011-01-01
So... I went into Synaptic and installed the KDE Help Center, since that was the error that I kept getting. Now it seems to work a little better. It will at least let me open Cervisia and KImageMap separately, though they still won't work as plug-ins within Quanta.

---

