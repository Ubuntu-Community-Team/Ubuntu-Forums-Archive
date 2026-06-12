---
title: "apt-cache"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by vipulkelkar on 2009-10-15
What is apt cache used for
How can i use apt-cache to try out stuff with packages

Thanks

---

### Post by hellblazer on 2009-10-15
I speak under correction, but as far as I understand apt cache is a cache of all the packages you've already downloaded. So if you need to reinstall something you've downloaded before, the package file doesn't need to be downloaded again.

A friend tells me that it also loads the list of available packages from the repositories.

---

### Post by ikisham on 2009-10-15
Open Terminal and type
```
man apt-cache
```

To exit the manual and get back to the Terminal, press 'q'.

---

### Post by Tomone on 2009-10-15
With apt-cache, I use the search function if I'm not sure of the exact name of the package I'm looking for. It looks through the software repositories.
```
apt-cache search <search-term>
```

---

