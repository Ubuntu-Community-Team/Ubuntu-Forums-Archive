---
title: "Dirvish for backup, problem with the lock_file -issue!"
date: 2023-09-01
forum: Networking &amp; Wireless
---

### Post by civilpolisen on 2023-09-01
We have three servers with Dirvish and on one the lock_file -issue appears next to daily now days! It's on different mashines... but usually on the second half of the list of servers to back-up.

Is there a solution and would it be possible to solve...?

```
 abe ....... success 20230831 113G 22.04 runbot v.2
 amber ..... success 20230831 42G  20.04
 barney .... success 20230831 38G  20.04 Mail (fd. Odoo 14, MÅ)
 bart ...... success 20230831 320G 20.04 LAMP/BlueSpice
 burns ..... success 20230831 299G 20.04 Odoo14 (drift)
 cyrus ..... success 20230831 139G 18.04 freeIPA
 edna ...... success 20230831 183G 20.04 GitLab 
 eliza ..... success 20230831 ???  18.04 Odoo12 
 gate ...... success 20230831 66G  18.04
 homer ..... success 20230831 ???  16.04 Odoo10 (drift)
 hugo ...... failure 20230831 62G  20.04 (docker/kubernetes) runboat
 lisa ...... success 20230831 ???  20.04 
 maggie .... success 20230831 198G 14.04 odoo8 (drift, ej IPA) e-mail(??)
 marge ..... success 20230831 230G 22.04 e-mail
 odooutv10 . success 20230831 68G  16.04
 odooutv12 . success 20230831 ???  18.04
 odooutv13 . failure 20230829 86G  18.04 <<<<<<<<<<<<<<<< lock_file was removed earlier in the morning!
 odooutv14 . success 20230831 ???  
 odooutv15 . success 20230831 66G  20.04
 odooutv16 . success 20230831 57G  22.04
 odooutv9 .. success 20230831 46G  16.04
 rita ...... success 20230831 26G  20.04 Prosody
 snowball .. ??????? never    12K  
 stanley ... success 20230831 ???  20.04 PowerDNS
 strand .... success 20230831 ???  20.04 KVM-server
 tull0 ..... success 20230831 ???  20.04 KVM-server
/dev/vdb        4.9T  4.5T  174G  97% /srv

```

Actually, when I now look at the back-up, Dirvish has backed up most servers any way! But I need to manually remove the lock_file for backup to complete the daily cycle!
Is there a way of solving this!?
I now notice that there is not much space left on the device... How much space is recomended to have free on the device!?

---

### Post by TheFu on 2023-09-01
Use LVM snapshots.

---

