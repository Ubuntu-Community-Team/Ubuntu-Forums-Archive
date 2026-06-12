---
title: "How can i download  and save the updates, but not install immediately?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by asaren on 2008-12-15
How can i download  and save the updates, but not install immediately?

On the update manager, it always install the updates directly.

Thank you

---

### Post by kcy29581 on 2008-12-15
Navigate to: System -> Administration -> Software Sources.

Then go to the "Updates" tab, and under the "Automatic Updates" section, make sure that "Download all updates in the background" is selected.

---

### Post by kpkeerthi on 2008-12-15
```
sudo apt-get update && sudo apt-get --download-only upgrade
```

---

### Post by asaren on 2008-12-15
What I want actually is download them first as files then install to other computers.

---

### Post by Michael.Godawski on 2008-12-15
hi asaren, 

have a look at these

[LIST]
[*][http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[*][http://aptoncd.sourceforge.net/ ]("http://aptoncd.sourceforge.net/")<-- especially this one
[/LIST]

---

### Post by kpkeerthi on 2008-12-16
> **asaren said:**
> What I want actually is download them first as files then install to other computers.

Use the 'install' command along with --download-only and the package and all its dependencies will be saved in apt cache folder.

---

### Post by albinootje on 2008-12-16
sudo apt-get -d install
is perhaps easier to remember

---

