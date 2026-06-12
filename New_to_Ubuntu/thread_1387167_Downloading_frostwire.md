---
title: "Downloading frostwire"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by afc1903 on 2010-01-21
Hi folks, first post.                                                                                                     I've tried to download frostwire, but receiving an error message 
Failed to install package 'frostwire-4.18.6.i586.deb'
In terminal it says: 'libxcb-shape0' is missing final newline
Any ideas what the problem is?
Thanks in advance.

---

### Post by bswilson on 2010-01-22
There are a few reports of that package being corrupted.  If you'll issue these 3 commands, you can fix the problem.  Afterward, you should be able to install Frostwire normally with no problem.

```
cd /var/lib/dpkg/info
sudo rm libxcb-shape0.list
sudo apt-get --reinstall install libxcb-shape0
```

---

