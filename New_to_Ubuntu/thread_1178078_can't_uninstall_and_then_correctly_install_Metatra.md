---
title: "can't uninstall and then correctly install Metatrader using Wine"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by Ubunser on 2009-06-04
I installed Metatrader but the fonts in news look the following way:

*Ïðåäñòàâèòåëü ÎÝÑÐ Ãóððèà: Ìåð ñòèìóëèðîâàíèÿ âî Ôðàíöèè äîñòàòî÷íî äëÿ ïîääåðæàíèÿ ýêîíîìèêè è çàíÿòîñòè

Everything else (panels) are written correctly in latin. But I need news. So, I tried to uninstall it, but maybe I don't know how. Cause clicking on Uninstall in Applications--Wine--Programs... doesn't work. 
Is there a way to totaly uninstall it using other methods like terminal? Thanks

---

### Post by durand on 2009-06-04
To remove all your wine settings, in a terminal, type:
```
rm -rf ~/.wine
```

---

