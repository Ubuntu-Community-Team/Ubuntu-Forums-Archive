---
title: "will this code help my situation"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by ubunguy on 2010-07-06
im trying to get ubuntu to see my internal sd card reader ,when i insert a sd card into it.

i have installed everything else dont really want to install another distro unless i have to

im using acer aspire one 532 

these are the codes i got  from another blog

/sbin/modprobe pciehp pciehp_force=1

or

sudo nano /etc/modules and add options pciehp pciehp_force=1

let me know thanks

---

### Post by jtarin on 2010-07-06
[Try here]("http://goinggnu.wordpress.com/2009/11/12/read-your-sd-card-with-your-ubuntu-laptop/")
[Or here.]("http://subbass.blogspot.com/2010/05/howto-ubuntu-1004-lucid-post-install.html")

---

### Post by ubunguy on 2010-07-07
i tried both and nothing happened so nether work  i just changed the one line and added the one line at the bottom of the page and restarted. if anyone has any ideas would be appreciated.


this is what i have


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
tifm_sd
lp






 did i do it right

---

