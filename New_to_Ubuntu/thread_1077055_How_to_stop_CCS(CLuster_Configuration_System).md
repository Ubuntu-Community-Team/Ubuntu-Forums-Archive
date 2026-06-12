---
title: "How to stop CCS(CLuster Configuration System) ?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by kshtjsnghl on 2009-02-22
Hi while playing through my synaptics two days back i kind of installed this CCS package. But after wards when i rebooted my system it kind stuck showing this problmem :

fence_tool : waiting for cman to start

I had to press alt+ctrl+del to get out of that loop. Then my system booted and i removed ccs from my system. But guess what today morning when i again booted my system it showed the same problem. Then i tried removing it but apt shows that it has already been uninstalled.

I went through the ps list of root  and ccsd popped up. the version information is this :

kshitij@kshitij-laptop:~$ ccsd -V
ccsd 2.99.09 (built Aug 26 2008 13:34:55)
Copyright (C) Red Hat, Inc.  2004-2008  All rights reserved.

Can anyone tell me how to remove this package so that the system does not stuck the next time i boot it.

---

### Post by kshtjsnghl on 2009-02-22
Also any information on how to edit the process which are started when the computer boots up.
 Similar to the startup.ini in windows xp.

---

### Post by kshtjsnghl on 2009-02-23
Can someone please help me out here...

---

### Post by kshtjsnghl on 2009-02-27
I hate to do this again but bump!!

---

### Post by bmadaras on 2009-03-02
Remove libvirt-bin I believe is the package, check the dependency on the ccsd package and virt packages will be listed.  As far as services that startup on boot, I believe you can install BUM boot up manager that will give you some of the services that will be starting or you can use the update-rc.d and invoke-rc.d commands

---

