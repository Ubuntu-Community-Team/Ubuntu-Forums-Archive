---
title: "Help wifi key / wpa-psk"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by keef247 on 2008-10-09
can't work this out.
dell inspiron 1520 dell 1395 wifi card...
can see the networks yet my network don't work:(
it is correct aswell.
whats going on. it is wpa-psk if that helps.
how do i sort this without wifi ill go back to vista...
also how do i save an edited line at the beginning on grub.
i press e and correct the hd0,1 line and then if i press escape or b and it doesn't save it so i have to do it each time when i boot:(
on 8.0.4

---

### Post by keef247 on 2008-10-09
> **keef247 said:**
> can't work this out.
dell inspiron 1520 dell 1395 wifi card...
can see the networks yet my network don't work:(
it is correct aswell.
whats going on. it is wpa-psk if that helps.
how do i sort this without wifi ill go back to vista...
also how do i save an edited line at the beginning on grub.
i press e and correct the hd0,1 line and then if i press escape or b and it doesn't save it so i have to do it each time when i boot:(
on 8.0.4

bumpy

---

### Post by Swagman on 2008-10-09
re: editing grub.

your doing it wrong.

Boot into your desktop.
Open a terminal ( Applications/accessories - terminal)

type ( copy & paste into terminal)

```

 sudo gedit /boot/grub/menu.lst

```

Now it will work !!

---

