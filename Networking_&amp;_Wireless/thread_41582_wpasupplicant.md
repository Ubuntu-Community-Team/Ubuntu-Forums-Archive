---
title: "wpasupplicant"
date: 2005-06-14
forum: Networking &amp; Wireless
---

### Post by Poyayan on 2005-06-14
I've been trying to download the wpasupplicant package but the package appears to be corrupt.  Is this going to be fixed anytime soon or does this apply to only me?

---

### Post by Seth on 2005-06-14
Hi Poyayan,

The US/CA archive is currently experiencing issues. To fix this, open a Terminal and issue the command:

**sudo gedit /etc/apt/sources.list**

And change all lines with [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) to [http://archive.ubuntu.com](http://archive.ubuntu.com)

Note that you just remove the "us." :-D

Have a great day!

---

