---
title: "Can't seem to find the index.html"
date: 2014-07-27
forum: Networking &amp; Wireless
---

### Post by Fertech on 2014-07-27
I'm running the 14.04 LTS Version on my computer and for some reason I can't seem to find the /var/www/index.html

---

### Post by SeijiSensei on 2014-07-27
The default web directory became /var/www/html in 14.04.  Look there.

---

### Post by Fertech on 2014-07-27
I can see the /var but there's no /www

---

### Post by Fertech on 2014-07-27
I'm trying to download apache2 but I get an error saying E: could not lock the /var/lib/dpkg/lock - open (11: resource temporarily unavailable )
E: unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by lisati on 2014-07-28
Forget looking for /var/www for now. Do you have two processes that install software running at once, e.g. software centre & synaptic?

---

### Post by Fertech on 2014-07-28
I just aware of software center

---

### Post by lisati on 2014-07-28
Were you trying to download/install apache2 through software centre, or were you using some other method?

---

### Post by Fertech on 2014-07-28
From the terminal

---

### Post by lisati on 2014-07-28
> **Fertech said:**
> From the terminal

Try closing the software centre before installing something from the terminal.

---

### Post by Fertech on 2014-07-28
I closed software center and was able to install apache, but I still have /www missing

---

### Post by Fertech on 2014-08-05
This thread was not been solved.

---

