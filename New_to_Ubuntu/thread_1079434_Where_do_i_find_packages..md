---
title: "Where do i find packages."
date: 2009-02-24
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-02-24
So i am trying to install wireshark and I can't find a package for it.

i tried apt-get but i don't have any others.
Is there a place to search for packages and the commands to download them?

---

### Post by UltraMathMan on 2009-02-24
You can search for packages either using the Synaptic Package Manager (System->Administration->Synaptic Package Manager) or with apt-get or aptitude. Personally I perfer aptitude for searching, in this case ```
aptitude search wireshark
``` and then apt-get to install.

-Hope this helps :)

---

### Post by taurus on 2009-02-24
Looks like wireshark is in the universe so make sure you have universe and multiverse enable in /etc/apt/sources.list.  Go into System -> Administration -> Software Sources and put a check mark for those repos.

[http://packages.ubuntu.com/search?keywords=wireshark&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=wireshark&searchon=names&suite=intrepid&section=all)

---

### Post by fenian on 2009-02-24
You can use Synaptic Package Manager to search for and install packages.To open Synaptic go to the menu System>Administration>Synaptic Package Manager.

---

### Post by wlraider70 on 2009-02-24
that worked great, thanks all.

---

