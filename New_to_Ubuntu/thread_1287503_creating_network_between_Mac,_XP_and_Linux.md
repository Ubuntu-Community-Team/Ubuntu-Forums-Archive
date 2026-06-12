---
title: "creating network between Mac, XP and Linux"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by Norman Thom on 2009-10-10
I have three computers attached to a router/modem
The XP has an Epson cx3810 attached to it
I would like to create a network amongst the three computers so that I might share documents and the printer on the XP.
I was thinking I would use the Linuz machine as server if I knew how
Can anyone advise me on what to do?

---

### Post by sandyd on 2009-10-10
> **Norman Thom said:**
> I have three computers attached to a router/modem
The XP has an Epson cx3810 attached to it
I would like to create a network amongst the three computers so that I might share documents and the printer on the XP.
I was thinking I would use the Linuz machine as server if I knew how
Can anyone advise me on what to do?
Linux:
```

sudo apt-get install samba system-config-samba
sudo system-config-samba

```
In the new window that appears, go to Prefrences -> Server Settings.

Enter your workgroup (all computers should have the same workgroup)
Then go to the security tab, and change authentication mode to "share"
Encrypt passwords : no
Guest Account : yourusername
click  "ok"

you can then add shares by clicking on the "+" button. (only on directories that you own though)

p.s.
you need to 

```

sudo /etc/init.d/samba restart

```
after setting up the shares.

---

### Post by Norman Thom on 2009-10-10
Thanks Carlee

I'm sure that's done it

---

