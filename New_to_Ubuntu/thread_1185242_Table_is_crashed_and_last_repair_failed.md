---
title: "Table is crashed and last repair failed"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by samjoseph74 on 2009-06-12
[COLOR=blue]When I am making certain modifications in the xyz table. While doing so, I encounter a power outage and my system shuts down unexpectedly. Again I switch on my system and try to open the table, the following error message gets displayed:[/COLOR]
  
  *[COLOR=blue]“Table is crashed and last repair failed”[/COLOR]*
   
  The data saved in the xyz table becomes inaccessible after the error occurrence.

---

### Post by freak42 on 2009-06-12
what kind of tables are you talking about?

---

### Post by lisati on 2009-06-12
[COLOR="White"]Does the power outage occur every time you modify table xyz? If so it could be a widespread hardware fault[/COLOR]

---

### Post by Davidpoul on 2009-06-15
To resolve the above error message, you will need to repair *xyz**.**myi* table by using these steps:
   
  
[LIST]
[*]To check and analyze the corrupted table, use either      of the two commands:
[/LIST]
  *myisamchk xyz**.**myi*
  Or
  *Check Table xyz*
  
[LIST]
[*]To repair the corrupted table, use either of the two      commands:
[/LIST]
  *myisamchk -r –q xyz (**-r -q** means “quick recovery mode”)*
  *Or *
  *Repair Table xyz*
   
  But if the above repair commands fail to repair the *xyz* table, you need to repair the table by using powerful [MySQL Repair]("http://www.repair-mysql-database.com") software. Such MySQL Database Repair applications incorporate advanced scanning algorithms to repair and restore the data stored in MyISAM tables.

---

