---
title: "Problem installing k9copy"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by laffinet on 2009-06-04
Hi !

I'm running Mythbuntu 9.04 from a fresh install and tried to install k9copy, however when I run

```
sudo apt-get install k9copy
```

I get the following errors

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  k9copy: Depends: kdebase-runtime (>= 4:4.1.96) but it is not going to be installed
          Depends: kdelibs5 (>= 4:4.1.96) but it is not going to be installed
          Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
E: Broken packages
```


I've got this line in the sources.list file:

```
deb http://au.archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse
```

Any idea what could cause this and what I can do to resolve this ?

When trying to install the package independently (sudo apt-get install kde-base runtime) I get the same error:

```
The following packages have unmet dependencies:
  kdebase-runtime: Depends: kdelibs5 (>= 4:4.2.1) but it is not going to be installed
                   Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
                   Depends: kdebase-runtime-bin-kde4 (= 4:4.2.2-0ubuntu1) but it is not going to be installed
E: Broken packages

```

---

### Post by Didius Falco on 2009-06-04
Hi,

Two things I'd try:

1. First thing I'd do is go to **Synaptic** and check for any broken packages that need to be resolved. If that doesn't do it, I'd then:

2. Open **Software Sources** and change servers. Generally, I find that the Main server will have things first, and then they get distributed out from there.

I hope it helps...

Regards,

Didius

---

### Post by laffinet on 2009-06-04
Tried both, doesn't change a thing. Thanks for the suggestion.

---

### Post by laffinet on 2009-06-04
Anyone else ? Any other ideas what's going on ? Thanks.

---

### Post by laffinet on 2009-06-08
Bump

---

