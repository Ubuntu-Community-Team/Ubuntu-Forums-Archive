---
title: "Upgrade error"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-06-06
I am trying to upgrade my packages through synaptic and the CLI and I get the following error:

```

Reading state information... Done
The following packages have been kept back:
  linux linux-generic linux-headers-generic linux-image linux-image-generic
  linux-restricted-modules linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

```

In synaptic upgrading one package requests that I upgrade another package, etc. etc.

Is there anyway to force the upgrade?

---

### Post by Mornedhel on 2009-06-06
Hello,

It's not an error per se, it just means that upgrading involves some non-trivial package management. Usually this happens when upgrading requires installing a new package, for instance if an application uses a new library.

In this case it's more of a SNAFU on the repositories as the dependencies are (version-wise) completely messed up. The recommended course of action is to wait until the situation resolves itself when the maintainers fix the dependencies.

---

### Post by abhiroopb on 2009-06-06
So suggestion is do nothing?

fair enough :)

---

