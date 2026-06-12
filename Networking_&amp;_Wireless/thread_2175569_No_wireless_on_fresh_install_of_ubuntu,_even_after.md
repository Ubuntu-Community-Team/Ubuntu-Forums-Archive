---
title: "No wireless on fresh install of ubuntu, even after wired update"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by Pedro_Teixeira_Spinola on 2013-09-19
Hey guys,

Not sure how to tell you what is the name of my network card, cause I don't know it.
I'm pretty much a begginer, and I have no wireless on my samsung laptop after a fresh install of ubuntu.
I did a wired update, tried to add drivers (got errors).
Tell me how to provide the needed information, please, so I can get help.


Thanks,
Pedro

---

### Post by Kirboosy on 2013-09-20
Welcome to the forums! 

Would you be able to try installing the drivers again but this time when the errors happen copy an paste them here so we can see the errors.

Thanks!
~Caboose

---

### Post by gopi_nath_vajpai on 2013-09-20
Hi Pedro,

I am pretty new to Lubuntu as well, however suggest you to run queries 'lspci' and 'lsusb' (without the quotes) and post the output so that people may see which wifi card you are using. Also send the error during installation as suggested by Caboose.

Cheers.

---

### Post by varunendra on 2013-09-21
> **gopi_nath_vajpai said:**
> I am pretty new to Lubuntu as well, however suggest you to run queries 'lspci'....

Or even better (and smaller), the output of -
```
lspci -nnk | grep -iA2 net
```
..plus 'lsusb', and of course what Caboose885 asked for.

---

