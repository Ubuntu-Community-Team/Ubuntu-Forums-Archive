---
title: "viewing vsftpd logs with gnome-system-log"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by ankara on 2007-01-11
this is not a real ](*,)  "problem" as such just an irritation i noticed while setting up vsftpd which i though i'd document as ive got 10 spare minutes ;) .

when i came to check the logs i typed code "sudo cat /var/log/vsftpd.log" and it displayed all the events i expected to see.

afterwards when i went to the Gnome system > administration > system logs program, i tried file > open and went to the vsftpd log at the above path and it would not open this file.

if this is bugging anyone else, the solution was simply to edit the menu item command to include "gksu" as a prefix to the existing "gnome-system-log" 

HTH

---

