---
title: "Evolution"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by jnmjr on 2010-03-01
Hey Guys,
After the latest Office upgrade I have a couple of e-mails that won't delete, these were there before the upgrade, the ones I read and delete after the the upgrade work fine, any one know what's up with that? It's annoying having five e-mails I can't delete. BTW I can't manually send them to any other folder.

---

### Post by philinux on 2010-03-01
> **jnmjr said:**
> Hey Guys,
After the latest Office upgrade I have a couple of e-mails that won't delete, these were there before the upgrade, the ones I read and delete after the the upgrade work fine, any one know what's up with that? It's annoying having five e-mails I can't delete. BTW I can't manually send them to any other folder.

In .evolution/mail/local is a file called folders.db

I seem to remember that deleting this file solves the problem.

Restarting evo recreated this database file. I would make a backup of evolution first. Or at least the folders.db file.

[http://library.gnome.org/users/evolution/stable/b17qy921.html.en](http://library.gnome.org/users/evolution/stable/b17qy921.html.en)

---

### Post by jnmjr on 2010-03-01
> **philinux said:**
> In .evolution/mail/local is a file called folders.db

I seem to remember that deleting this file solves the problem.

Restarting evo recreated this database file. I would make a backup of evolution first. Or at least the folders.db file.

[http://library.gnome.org/users/evolution/stable/b17qy921.html.en](http://library.gnome.org/users/evolution/stable/b17qy921.html.en)

THX Phil worked, that file must have been currupted by the update...

---

