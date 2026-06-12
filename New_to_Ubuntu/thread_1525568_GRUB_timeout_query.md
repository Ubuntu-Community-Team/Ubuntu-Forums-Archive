---
title: "GRUB timeout query"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by Miguellint on 2010-07-06
Hi all...I want my GRUB bootup menu to *NOT* timeout after however many seconds but to sit waiting for user input.

Should I change the menu.lst timeout setting to something like ten billion seconds or is there a more elegant way.

Thanks
Miguellint

---

### Post by Darkness Des on 2010-07-06
Change the timeout to -1. I've only tried this on Grub2, but it might work on Legacy.

---

### Post by Miguellint on 2010-07-06
> **Darkness Des said:**
> Change the timeout to -1. I've only tried this on Grub2, but it might work on Legacy.

Works a treat. Thanks very much :-)

---

