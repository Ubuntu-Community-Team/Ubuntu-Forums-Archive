---
title: "My wireless Icon Is missing?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by atopthemountain on 2009-04-23
Im using an Asus EeepC 701 i dont know where to chek what version of unbuntu i have (its like GOME 8.0 i think)

My mouse malfunctioned and removed (i have no idea how ) my wireless icon. I know it can pick up signals buti it still does not log on the internet...and even if it coould i wouldnt be able to knw what server or action pointo to locate.......

please help

---

### Post by Tahakki on 2009-04-23
Right click the panel, click 'Add to Panel...' and choose Notification Area.

---

### Post by Peter09 on 2009-04-23
Try running in a terminal

```
nm-applet --sm-disable
```

also

got to

System->Preferences->Startup Applications ( or Sessions in earlier version)

See if the network manager task is ticked to start at login.

EDIT: It could be Tahakki's suggestion as well, you'll have to see which works.

---

### Post by atopthemountain on 2009-04-23
Thank you both for your response.
I tried Tahakki's suggestion first and it worked!!!!

:guitar:

---

