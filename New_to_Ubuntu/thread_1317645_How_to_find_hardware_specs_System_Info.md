---
title: "How to find hardware specs? System Info?"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by onthefence on 2009-11-06
Is there a place to find the whole list of what hardware your computer has?

In System Monitor, I can see Memory, CPU, and available disk space. Is that all we get?

thanks

---

### Post by PKinPA on 2009-11-06
in a terminal type
lspci
that may give you the info your looking for.

---

### Post by onthefence on 2009-11-06
ok, yeah, it's not going to win the beauty contest in the formatting contest, but that may do. I am selling the computer and just want to include as many details as possible. 

thanks

---

### Post by winotree on 2009-11-06
In terminal ```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
``` prints to screen and gives report in your *user* file.  Many thanks to **louieb**.

---

### Post by onthefence on 2009-11-06
Now that's pretty.

Thanks winotree, and thanks to louieb as well.

I'm still a little surprised that the feature isn't built into the System Menu. But whatever.

---

### Post by Darce on 2009-11-06
You can always go to the Software Centre or Package Manager and install 'Device Manager'

---

