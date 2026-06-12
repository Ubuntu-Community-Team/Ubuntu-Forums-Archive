---
title: "[SOLVED] lm-sensors"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by xieu90 on 2008-12-03
hi everyone
i installed lm-sensors and i get this picture
what is temp 1 ?
and why is it minus 48 grad ?
i am using asus crosshair mainboard.

---

### Post by Michael.Godawski on 2008-12-03
Taken from


[LIST]
[*][http://www.lm-sensors.org/wiki/FAQ/Chapter3#WhydomytwoLM75sreport-48degrees](http://www.lm-sensors.org/wiki/FAQ/Chapter3#WhydomytwoLM75sreport-48degrees)
[/LIST]

> **Why do my two LM75's report "-48 degrees"?[ ¶]("http://www.lm-sensors.org/wiki/FAQ/Chapter3#WhydomytwoLM75sreport-48degrees")**

  For starters, those aren't LM75's. Your mainboard actually has the Winbond W83781D which emulates two LM75's, but many systems which use the Winbond chip (such as the Asus P2B) don't have the thermo-resisters connected to the chip resulting in these strange -48 degree readings. 
  In upcoming versions, you will be able to disable non-interesting readings. 


---

### Post by xieu90 on 2008-12-03
thank you
so it means -48 is nothing and not that important and i can remove that , right ?

---

### Post by Michael.Godawski on 2008-12-03
I guess yes. ;)

---

### Post by xieu90 on 2008-12-03
thank you

---

