---
title: "bit confused about apache"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by kapi on 2009-02-13
feel a bit stupid, seems to happen a lot while learning Ubuntu!

so here we go, tried installing lamp then had problems with the DPKG but then ran the update manager and apache seemed to load.it even asked me to input a root password.

but. . what next? is that it do I go to a specific file to see where I store files? How do I test to see if everything works?

Thanks for listening

Kapi

---

### Post by mcduck on 2009-02-13
Open your web browser and go type "localhost" to the address bar. You should see Apache's default page.

All files go to /var/www, although you can easily change this or add new web directories with "a2ensite" command.

---

### Post by Tibuda on 2009-02-13
I recommend you to install [rapache]("apt:rapache"), which is a GUI to manage your apache sites and enable/disable modules.

---

### Post by kapi on 2009-02-13
Thank you, its seems to work, the words " it works" are displayed

kapi

---

