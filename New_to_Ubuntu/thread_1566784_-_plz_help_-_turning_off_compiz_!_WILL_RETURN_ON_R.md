---
title: "- plz help - turning off compiz ! WILL RETURN ON RESTART"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by Objectivity on 2010-09-02
Hi folks,

 EACH TIME I turn off compiz and SELECT ( Appearance preferences - None - Provides a simple desktop environment without any effects ) 

 IT WILL return on restart to NORMAL ! 

I want Compiz removed or stay on NONE forever since my laptop slows down dramatically when is on. 

 SO OS much thankS .

---

### Post by llawwehttam on 2010-09-02
Go to System>Preferences>startup Applications

Remove compiz if it is there.

if its not there please press "add"

give it the name"metacity" and the command ```
metacity --replace

```
press save and then try logging out.in again.

---

### Post by Objectivity on 2010-09-02
> **llawwehttam said:**
> Go to System>Preferences>startup Applications

Remove compiz if it is there.

if its not there please press "add"

give it the name"metacity" and the command ```
metacity --replace

```press save and then try logging out.in again.


 ::: FANTASTIC ::: solved ! I restarted my computer and now is just fine. It is set on NONE.

 Thank you so much :popcorn:

---

### Post by llawwehttam on 2010-09-02
your very welcome.

Its not really a proper fix as it were but it works.

To explain what it does; 

As compiz runs automatically, the added startup script replaces it just after it starts so compiz technically runs...... for a short time..

---

### Post by Objectivity on 2010-09-02
> **llawwehttam said:**
> your very welcome.

Its not really a proper fix as it were but it works.

To explain what it does; 

As compiz runs automatically, the added startup script replaces it just after it starts so compiz technically runs...... for a short time..


   

 Thanx anyways :KS

---

