---
title: "how to solve error message problem"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by keith brittany on 2009-02-02
New installation of ubuntu shows error message when I try to use synaptic package manager. It says that file h/1650/pr is corrupt and/or not archived and then refuses to do anything else. Same with update manager

help please

---

### Post by billgoldberg on 2009-02-02
Run 

```
sudo apt-get update && sudo apt-get upgrade
```

in a terminal (applications -> accessories -> terminal), and copy/paste the error here.

---

### Post by leonardo_neo on 2009-02-02
> **keith brittany said:**
> New installation of ubuntu shows error message when I try to use synaptic package manager. It says that file h/1650/pr is corrupt and/or not archived and then refuses to do anything else. Same with update manager

help please


Try this

> sudo apt-get update

---

### Post by keith brittany on 2009-02-02
> **billgoldberg said:**
> Run 

```
sudo apt-get update && sudo apt-get upgrade
```

in a terminal (applications -> accessories -> terminal), and copy/paste the error here.

thanks. I tried your solution but it now says "unspecified error" in the update manager and still asks me to remove and manually update corrupt file h/1650/pr any offers?

---

