---
title: "Package updte requests"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by SteelCore on 2010-02-10
One often notices outdated packages in the repositories like The Sleuthkit for example. What is the process to make a request or reminder for updating?
Thanks

---

### Post by Satoru-san on 2010-02-10
> **SteelCore said:**
> One often notices outdated packages in the repositories like The Sleuthkit for example. What is the process to make a request or reminder for updating?
Thanks
Its not ubuntu that is behind necessarily, it could very well be debian that hasnt made a .deb for the program yet, you can find out by googling 
```
site:packages.debian.org <package name> + <arch>
```

If you do find what you want, then install the .deb.

If not then hound debian, or make a request.

---

### Post by mikewhatever on 2010-02-10
The way Ubuntu, and most other distros, work, is that most packages are upgraded with every new release. That means, most of the packages in the repositories are outdated, and you have to wait for the next release to get a version bump or compile yourself. Other popular routs are backports and ppa repositories.

---

