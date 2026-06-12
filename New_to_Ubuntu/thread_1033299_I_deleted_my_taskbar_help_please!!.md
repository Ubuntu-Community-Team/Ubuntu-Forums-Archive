---
title: "I deleted my taskbar help please!!"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by MaximoMilkman on 2009-01-07
Im off of school today due to bad weather.. so i decided to fool with xubuntu and then i deleted my applications taskbar both bottom and top how do i get the back.. any terminal codes or something??? please help i am a lost puppy in linux!!

---

### Post by sisco311 on 2009-01-07
to add a new panel go to: Applications -> Settings -> Settings Manager -> Panel

to restore the default panels, open a terminal and type:
```
mv ~/.config/xfce4/panel/ ~/.config/xfce4/panel-backup
killall xfce4-panel
```

press Alt+F2 and run: *xfce4-panel*

---

### Post by MaximoMilkman on 2009-01-07
cisco i love you like a fat kid loves cake now!!!!!!!!!! i love you so much its people like you that make me never want to boot windows again!!! many thanks from the UNITED STATES!

---

### Post by sweetmiracle on 2009-11-02
Thank you, thank you, thank you!

So simple, even a semi-noob can do it!

---

