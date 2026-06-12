---
title: "Update Manager Error"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by Sleven7 on 2010-09-06
When I used the update manager I got the following error message,

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Is this a concern?  If so how is it corrected?

---

### Post by Ozymandias_117 on 2010-09-06
> **Sleven7 said:**
> When I used the update manager I got the following error message,

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Is this a concern?  If so how is it corrected?

It's not a huge problem, but to make it stop saying it, do this:

```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

This is installing the package medibuntu-keyring which contains the public key for medibuntu. The switches are just telling apt-get it is allowed to install this package that can't be authenticated (Because we don't have a public key yet). Then updates your package list which can now be authenticated.

---

### Post by Sleven7 on 2010-09-06
Thanks Ozymandias, that seems to have worked. The error message no longer displays.

---

