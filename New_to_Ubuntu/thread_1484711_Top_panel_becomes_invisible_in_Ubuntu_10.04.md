---
title: "Top panel becomes invisible in Ubuntu 10.04"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by SACHINVD on 2010-05-16
Hello !
1 week ago i installed ubuntu 10.04.
It was not having any problem till today .. but today i don't know how but
top default panel becomes invisible.
But it is working as when i press "Alf+f1" it shows application menu and subsequently
shows others menu to when i move mouse over their locations.
what is the problem ?

Thank You !!!

---

### Post by kio_http on 2010-05-16
Do you have an NVIDIA graphic card?

If you wish to try resetting GNOME to its defaults.
NOTE: You won't lose documents, software etc but all custom settings of GNOME wil go.
Applications Menu > Accessories > Terminal
```
rm -rf .gnome
```

---

### Post by SACHINVD on 2010-05-16
I have intel graphics card.
Compiz is having problem with it so installed another Composite
manager keeping compiz as it is.

so do i need to uninstall compiz ?

Thank You !!!

---

### Post by kio_http on 2010-05-16
> **SACHINVD said:**
> I have intel graphics card.
Compiz is having problem with it so installed another Composite
manager keeping compiz as it is.

so do i need to uninstall compiz ?

Thank You !!!
Did this problem occur after you started using desktop composition?

---

### Post by SACHINVD on 2010-05-16
Problem started after 2-3 days i installed cairo composite manager.

---

