---
title: "uninstall"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by The Green Tiger on 2011-08-03
72yr old just starting Linux so please treat kindly.

Wanted to uninstall program from the desktop mode. put icon in bin then could not find any trace of said item, there were still older items in bin but this one had gone. (a) why is this? (b) how can I cleanly uninstall from desk top?

---

### Post by Rex Bouwense on 2011-08-03
Hey Tiger.  The icon on the desktop is merely a shortcut.  If you want to remove a program from your computer you need to do that from the terminal, the Ubuntu Software Center, or the Synaptic Package Manager.

---

### Post by Bucky Ball on 2011-08-03
System>Administration>Synaptic Package Manager. 
Search for the program you want to uninstall,
Click box next to it, mark for removal (or complete removal if you never intend to use it again),
Click 'Apply'.

 Done. ;)

---

### Post by amjjawad on 2011-08-03
And if you would like to do that from Terminal:

```
sudo apt-get purge <packagename> 

```

I guess Synaptic Approach is the easiest one.

---

