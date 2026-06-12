---
title: "Why do i have apache2?"
date: 2015-10-09
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2015-10-09
I am having some boot error messages including one relating to Apache2. 

Should I uninstall apache2?

I have a desktop machine AMD 64. I use virtualbox and teamviewer and wonder if that is why I have it installed. I also use rygel to play media on my TV that is stored on  my Computer's  HD  ([https://wiki.gnome.org/Projects/Rygel/Features](https://wiki.gnome.org/Projects/Rygel/Features)) Thunderbird gets my email via pop3 to gmail.

---

### Post by michi1983 on 2015-10-09
When you don't need it, just uninstall it :-)

---

### Post by buzzingrobot on 2015-10-09
Apache was likely pulled in as a dependency for a package you've installed. If you want  remove it, pay attention to the other packages apt-get wants to remove.

 You might start another thread posting the specific error messages you are seeing.

---

