---
title: "How do I remove a useless 'Ubuntu' option from my boot screen?"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by todzak on 2011-02-15
On my HP laptop, I had Windows 7 Home Premium dual booting with Ubuntu 10.04 (Wubi). Then I did a fresh install of Windows 7 Professional, and then reinstalled Ubuntu as dual boot (also via Wubi, but 10.10 this time), but unfortunately I didn't uninstall the old Wubi before I did all the new installs. Now my Windows 7 Pro and Ubuntu 10.10 are working just fine, but I have a useless 3rd option when I boot up for the 'Ubuntu' that I *don't have anymore*. 
How do I get rid of that option on the boot-up list? It's rather annoying.

---

### Post by bcbc on 2011-02-15
Use easybcd to edit the boot menu, or microsoft's command line tool: bcdedit.exe

---

### Post by Mark Phelps on 2011-02-16
You get EasyBCD from the NeoSmart Technology forums.  It's a free download.  Be sure to get the latest version.

---

### Post by todzak on 2011-02-16
EasyBCD worked great! Thanks a lot. It's quite the little handy program. :)

---

