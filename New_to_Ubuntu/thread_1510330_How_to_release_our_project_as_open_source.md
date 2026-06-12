---
title: "How to release our project as open source"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by kapmsd on 2010-06-15
Hi guys.
My team of 3 members have completed the project "System Restore in Linux" with good insights obtained from this forum.So far we have developed for Ubuntu alone.
We used C coding and Qt for GUI.
We want to release this as an open source.
We would like our software to be included in the system repositories.
How to do it?

---

### Post by Bachstelze on 2010-06-15
Basically, you must include in your source tarball the license under which the code is released. There might be license-specific requirements so we can't tell you exactly what to do if you don't tell us which license you plan to use.

Then if you want your software in the repositories, you can either package it yourself and have it reviewed, or file a Wishlist bug and wait for someone to do it.

---

### Post by srs5694 on 2010-06-16
Having a package included in Ubuntu is fine, but unless it's really Ubuntu-specific (which despite the fact that you specified you used Ubuntu as a development platform, I doubt), you may want to consider releasing the package on a more general site. For instance, [Sourceforge](http://sourceforge.net/) or [Google Code.](http://code.google.com/) These sites provide hosting for open source projects and can make them visible and accessible to a wider audience than you'd get trying to release through Ubuntu alone. Note that releasing via Sourceforge, Google Code, or a similar site does not preclude submitting your project to Ubuntu. It might even facilitate it. (I don't know what Ubuntu's guidelines are, but if they like to see an independent site with the source code, having it on one of those sites will help.)

---

