---
title: "Terminal Command check / Update / Upgrade"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-18
What do we type into a terminal to check our repositories, make updates where needed and upgrade the packages?

What is the difference between updating and upgrading?

Thank you!

---

### Post by hovzio on 2009-04-18
sudo apt-get update && sudo apt-get upgrade

The difference, update just updates your package cache for the repos in your sources list. Upgrade installs the updates.

---

### Post by Crandom on 2009-04-18
Update brings the list of packages up to date, Upgrade actually installs new versions of the packages.

You need to update first before upgrading.

---

### Post by yeehi on 2009-04-18
So should I type:

```
sudo apt-get upgrade && sudo apt-get update

```

---

### Post by KIAaze on 2009-04-18
No, it's the other way around:
```
sudo apt-get update && sudo apt-get upgrade
```
:)

---

