---
title: "virtualbox deinstall problem"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by Achilles124 on 2010-03-22
I tried to deinstall virtual box with > sudo apt-get remove --purge virtualbox.


I get an error saying that virtualbox is not installed at all. Then I run virtualbox in the terminal and the program starts!??!!!

I ran sudo updatedb. But that didn't work. Same error. I rebooted. That didn't work either.

What can I do to completely remove virtual box from my machine?

---

### Post by r-senior on 2010-03-22
I think it might be listed under the version number:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
$ sudo apt-get install virtualbox
Package virtualbox is a virtual package provided by:
  virtualbox-3.1 3.1.4-57640_Ubuntu_karmic
  virtualbox-3.0 3.0.12-54655_Ubuntu_karmic
  virtualbox-2.0 2.0.12-53697_Ubuntu_karmic
You should explicitly select one to install.

```

Might be easiest just to find it in Synaptic and mark for complete removal?

---

### Post by Achilles124 on 2010-03-22
Yes, right on. Solved the problem. Thank you for answering.

---

