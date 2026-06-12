---
title: "GtkOrphan is it dangerous to remove all orphan packages?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by jingo811 on 2009-10-29
[SIZE="4"]Intro[/SIZE]

I'm following this guide and have questions regarding GtkOrphan specifically not all the other stuff.
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

Do a search with Firefox to see where I'm stuck.
> Firefox > ***Ctrl + f*** > "select the orphaned"


When I follow Ubuntugeek's guide then the "Orphaned packages TAB" is empty on my system so I read this guide instead about expanding <Options> and selecting **"Show all orphan packages"**.
[http://www.marzocca.net/linux/gtkorphan.html](http://www.marzocca.net/linux/gtkorphan.html)

Do a search with Firefox to see where I'm reading.
> Firefox > ***Ctrl + f*** > "How to use GtkOrphan"




[SIZE="4"]Questions[/SIZE]

So I don't really understand marzocca's description of howto use GtkOrphan when using that <Options> procedure. :)

**Q1**
Is it dangerous to remove all orphan packages with the "Show all orphan packages" option switched on?

**Q2**
Because I see a lot of important packages like these, so can I just remove everything that's listed without breaking my system?

**(OK to remove these in "Show all orphan packages"?)**
* acpi
* acpi-support-base
* flashplugin-nonfree
* gtkorphan
* iptables
* kernelloops
* linux-image-2.6.26
* linux-image-2.6-868
* localepurge
* manpages
* nano
* openbsd-inetd
* openoffice.org
* telnet
* xorg

---

### Post by earthpigg on 2009-10-29
an 'orphaned' package is just a package you have installed that no other packages depend on... that doesn't mean you the user do not depend on them, though.

off the top of my head:

keep xorg, that provides your graphical interface

keep nano, you may not NEED it right now, but if your graphical interface ever dies you will want a terminal-based text editor

keep open office if you use open office...

keep the man pages unless you have a photographic memmory and have them all memmorized.


ya, sooo i wouldn't get rid of any of those.

---

### Post by jingo811 on 2009-10-29
> **earthpigg said:**
> an 'orphaned' package is just a package you have installed that no other packages depend on... that doesn't mean you the user do not depend on them, though.

...
...

ya, sooo i wouldn't get rid of any of those.

So that's why everything started to disappear a few years ago when I used GtkOrphan.  I removed orphans once, then there were new orphans so I removed them twice, then there were some more new orphans.  I kept repeating this until everything was all kaput. ;)  I'll try to be more careful in the future with this program.  

Thanks for the explanation now I understand how it works.

---

### Post by earthpigg on 2009-10-30
i am ***not a fan at all*** of the gtkorphan ***or*** the janitor app.

people always seem to think this is windows with all sorts of rubbish everywhere by default, and start removing stuff without researching wtf it is.

---

