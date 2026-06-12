---
title: "Installing new program"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Jasper7g on 2009-06-15
I want to install a new program but haven't been able to find it by "search" in the Synaptic Package Manager, so I downloaded a Linux version from the site via windows. It is called Express Scribe (scribe.tar.gz). It is now on my desktop. How do I install it?

---

### Post by kballero on 2009-06-15
most likely:
# tar -xvzf scribe.tar.gz

# ./scribe

voila!

---

### Post by SunnyRabbiera on 2009-06-15
looks quite simple here, you unzip the file and click the install script inside.
No compiling needed it seems, thats cool.

> **kballero said:**
> most likely:
# tar -xvzf scribe.tar.gz

check if there is a README or INSTALL file
You will most likely need to compile.
# ./configure

# make && sudo make install

voila!

Doesnt look to be the case, but the terminal might be needed as this seems to want administation access.
Still installation of this one looks simple

---

### Post by kballero on 2009-06-15
awesome!

---

### Post by Jasper7g on 2009-06-15
Thanks. It's easy when you know how! :-) I don't know anyone near me who uses Linux, so no one to show me the basics.

---

### Post by SunnyRabbiera on 2009-06-15
> **kballero said:**
> awesome!

Indeed, for this app I would suggest the original poster install nautilus open terminal and gksu nautilus with synaptic.
Log out and then the ability to use administration access should be a little more easier.

> **Jasper7g said:**
> Thanks. It's easy when you know how! :-) I don't know anyone near me who uses Linux, so no one to show me the basics.

Well that is why we are here

---

