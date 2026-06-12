---
title: "Upgrade Ubuntu Software Center"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by mablake21 on 2010-11-25
Hello All,

I was wondering if there was a way to upgrade the Ubuntu Software Center without upgrading from 10.04 to 10.10. I am content with 10.04 and have no wish to upgrade. However the new features of the Software Center intrigue me and I would like to check them out.

Thanks

---

### Post by Locke_99GS on 2010-11-25
Grab the "software-center" package for Maverick from [http://packages.ubuntu.com](http://packages.ubuntu.com) and try to install it. You may or may not need to pull in a bunch of other stuff to make it work though

---

### Post by mablake21 on 2010-11-26
Error: Dependency is not satisfiable: gconf2 (>= 2.28.1-2)

---

### Post by Locke_99GS on 2010-11-26
I was afraid of that. You could try to also grab the Maverick version of gconf2 the same way, but you'll probably run into dependency hell with that as well, or you could luck out and that would be all that is required. 

If you could grab the source of software-center (assuming it's not interpreted) you could try compiling it against your current setup - beyond that, it may be easier to just install Maverick.

---

