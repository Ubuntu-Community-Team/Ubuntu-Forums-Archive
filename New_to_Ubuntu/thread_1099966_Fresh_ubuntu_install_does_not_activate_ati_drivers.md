---
title: "Fresh ubuntu install does not activate ati drivers"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Art3mis on 2009-03-18
Hi everyone,

I just did a fresh install of UBUNTU 8.10, when clicking on <activate>, ATI driver, nothing happens,   


What should I do??

---

### Post by sandyd on 2009-03-18
same thing for me....

did it this morning and NOTHING showed up

gave up instantly and installed driver using envyNG

---

### Post by kidux on 2009-03-18
Try clicking activate until it actually downloads the driver and installs it (which could be a bit), then you'll have to make the kernel use the new modules which can be accomplished through modprobe but may just be easier to reboot. After that it should work.

---

### Post by markbuntu on 2009-03-18
It is absolutely critical to get all the updates and reboot before trying to use that driver. Updates should be automatically offerd but if they are not use update manager and click check. After you reboot you should be able to enable that driver.

---

