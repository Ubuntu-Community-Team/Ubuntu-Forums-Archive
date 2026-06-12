---
title: "created a file but cant save it to specified dir need permission"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by richie1913 on 2009-07-05
I am in the middle of trying to get through a workthrough while the Instructions are clear they dont always explain how to do certain things like I need to create a file called /etc/udev/rules.d/999-zte.rules I did this and created a file called 999-zte.rules and the text to go in it but when i try and save the file to /etc/udev/rules.d It says I lack permission to to It and I cant create the file while In that dir as that option Is blanked out.Thanks again

---

### Post by ddrichardson on 2009-07-05
> **richie1913 said:**
> I am in the middle of trying to get through a workthrough while the Instructions are clear they dont always explain how to do certain things like I need to create a file called /etc/udev/rules.d/999-zte.rules I did this and created a file called 999-zte.rules and the text to go in it but when i try and save the file to /etc/udev/rules.d It says I lack permission to to It and I cant create the file while In that dir as that option Is blanked out.Thanks again
```
gksudo gedit /etc/udev/rules.d/999-zte.rules
```

---

### Post by richie1913 on 2009-07-05
Thanks very much.

---

