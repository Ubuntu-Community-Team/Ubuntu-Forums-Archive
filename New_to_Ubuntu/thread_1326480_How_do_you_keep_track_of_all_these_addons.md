---
title: "How do you keep track of all these addons?"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by JREAM on 2009-11-14
You guys I've gone through so many add-ons, like
"sudo apt-get install nautilus-gksu nautilus-open-terminal"

okay, I don't know how Im going to remember all these if I ever need to reinstall.
Is there some way to keep track of this, or should I write a list of commands Im doing?

LOL because there are a lot of things that are just hard to keep track of,
if you ever have to reinstall Linux how do you know all the settings and stuff you used?

---

### Post by jbrown96 on 2009-11-14
If you backup your home folder that will save all of the application settings, which is really nice. I believe there is something called apt-on-cd that you can use to backup your packages. There is also a way to export a list of packages, then you can run an apt command to install them. Unfortunately, I don't have specifics on what to do. Try searching for apt-on-cd and that should help you find some resources.

---

### Post by falconindy on 2009-11-14
You can run "dpkg --get-selections > dpkg.list" which will create a text file with a list of your installed programs. After a reinstall, "sudo dpkg --set-selections < dpkg.list" will restore this list.

---

### Post by jbrown96 on 2009-11-14
> **falconindy said:**
> You can run "dpkg --get-selections > dpkg.list" which will create a text file with a list of your installed programs. After a reinstall, "sudo dpkg --set-selections < dpkg.list" will restore this list.

This.

---

### Post by JREAM on 2009-11-14
AWESOME Thanks!! I bookmarked this for later :)

---

