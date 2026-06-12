---
title: "chkconfig"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by Diametric on 2009-12-10
Is there a reason why chkconfig is not available from a terminal?  I tried to run "/sbin/chkconfig --list" and I was directed to download it.  For full disclosure, I am working through a Redhat9 book on a Ubuntu machine.  Has chkconfig been removed since then?

---

### Post by jbrown96 on 2009-12-11
chkconfig is a red hat derivative thing. In 9.10, you can just run ```
start gdm
``` or ```
stop gdm
``` or whatever service you are trying to alter.

Ubuntu (and many other distros) are in the process of switching away from the old system scripts. I don't fully understand it, but Ubuntu should have completely made the switch by 10.04. 

Expect this stuff to be in a state of transition for the next year or so. 

This is one of the main problems with Linux books is that they tend to age very quickly. They aren't good for much beyond the basics. Linux tends to make substantial changes frequently.

---

