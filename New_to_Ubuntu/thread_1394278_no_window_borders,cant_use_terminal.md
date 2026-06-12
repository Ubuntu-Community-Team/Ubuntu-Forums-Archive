---
title: "no window borders,cant use terminal"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by soryu on 2010-01-30
i turned on my pc today and there are no window borders and when i open a terminal it's all white?
compiz plug ins are enabled.

---

### Post by wojox on 2010-01-30
Go to System > Preferences > CompizConfig Settings Manager and make sure the Window Decorations plugin is checked.

---

### Post by soryu on 2010-01-30
checked,enabled

---

### Post by MelDJ on 2010-01-30
try refreshing compiz

---

### Post by soryu on 2010-01-30
how do i refresh?

---

### Post by sisco311 on 2010-01-30
Press Alt+F2 and run:
```
metacity --replace
```
or if you are using emerald:
```
emerald --replace
```

---

### Post by soryu on 2010-01-30
thank's sisco fixed it  borders and terminal back. on to my next prob.

---

### Post by soryu on 2010-01-30
well ,i restarted and had to do the same thing.alt+f2 metacity- --replace.

how do  i make it startup  normally?

---

### Post by falconindy on 2010-01-30
In your Window Decorator plugin options should be a text box that specifies the window decorator command. If this is blank, add 'metacity --replace'.

---

### Post by soryu on 2010-01-30
restarted my pc  again and the borders are there.

there is a command there but it is /usr/bin/compiz-deco

ill restart  again if the borders dont show up i will change it.thank's

it's weird that plug-in has been enabled and i haven't touched it.

---

