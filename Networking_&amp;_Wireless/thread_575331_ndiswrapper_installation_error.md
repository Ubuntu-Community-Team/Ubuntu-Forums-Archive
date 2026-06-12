---
title: "ndiswrapper installation error"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by ghanchi on 2007-10-13
i installed ubuntu 7.10 rc and am trying to get my wireless network card to work, belkin f5d7000. im completely new to linux so im not sure if theres an obivious way to get my card to work.
so i downloaded ndiswrapper 1.48. but the first command in the install instructions isnt working
when i type
```

tar -zxvf ndiswrapper-1.48.tar.gz

```
i get an error that says no such file or directory. the file i downloaded is on my desktop, is it supposed to b  somewhere else?

---

### Post by jonathanmotes on 2007-10-13
Since the file is on your desktop, you have to change to the Desktop directory in the terminal before running the command you have. So do this:```
cd Desktop
``` then```
tar -zxvf ndiswrapper-1.48.tar.gz
```

This should extract the folder to your Desktop. When you open Terminal, it defaults to your home folder (or directory). If you didn't want to enter the "cd Desktop"  just copy your file to your home folder first.

---

