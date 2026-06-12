---
title: "Messed up title bars"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Sriram137 on 2010-10-24
Well,i was installing cairo-dock,and enabled compiz icon on it,and suddenly,BOOM.My title bar changes to red and looks darn ugly,i cant seem to change it even in the theme customization tab.It looks like a emerald thing,i am not sure.Pls help. :confused:[IMG]http://tinypic.com/r/207kmj4/7[/IMG]

---

### Post by howefield on 2010-10-24
Try in terminal

> compiz --replace

Failing that, a screenshot might be helpful.

---

### Post by Sriram137 on 2010-10-24
The solution didnt help.
Here is the SS.

---

### Post by howefield on 2010-10-24
Yep, that looks like an Emerald theme, you should be able to use either
```
compiz --replace
```
or
```
metacity --replace
```

in terminal to get back to your starting point.

---

### Post by Sriram137 on 2010-10-24
Well,it kinda partially works.

If i run metacity --replace,the task bars become normal for a while(compiz setting don't occur though),but i as soon as i close the terminal,all the titlebars disappear and cant even alt-tab. Have to force restart.

---

