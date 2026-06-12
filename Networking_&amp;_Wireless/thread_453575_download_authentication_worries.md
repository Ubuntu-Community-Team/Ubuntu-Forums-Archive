---
title: "download authentication worries"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by 900donuts on 2007-05-24
some thing odd is up with my computer all the software i try to get through synaptic or add/remove isn't getting authenticated i make my choices i hit apply it screams that the selected software can't be authenticated and i download it any way nothing bad has happened yet but i'm worried

a little help?

---

### Post by benanzo on 2007-05-24
This usually means that the repository you're downloading the packages from offer GPG keys that you can get which will be used to authenticate the origin/maintainer of that repo as legit.  However, in this case which ever repo you're downloading from does not require you to have the GPG key, so apt is just telling you that no authentication is going to be performed.  It is generally harmless, but you might look into where to obtain the keys for that  repo, otherwise it's possible for someone with access to their server to plant dummy packages without you being the wiser.  That's why the GPG authentication is important.  The true maintainer/packager will sign the packages with their private key and then offer their public key to users, which they use to verify that the packages are legitimate.

---

