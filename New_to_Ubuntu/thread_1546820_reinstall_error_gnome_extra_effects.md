---
title: "reinstall error gnome extra effects"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by stupidtrooper501 on 2010-08-05
i accidentally uninstalled gnome extra effect and when i try to reinstall using software center it tells me i need gnome and when i ty to install gnome with synaptic i get  			 				  gnome: Depends: swfdec-mozilla but it is not going to be installed i need help!

---

### Post by Ozymandias_117 on 2010-08-05
> **stupidtrooper501 said:**
> i accidentally uninstalled gnome extra effect and when i try to reinstall using software center it tells me i need gnome and when i ty to install gnome with synaptic i get  			 				  gnome: Depends: swfdec-mozilla but it is not going to be installed i need help!

Try this in a terminal:
```
sudo aptitude update && sudo aptitude install gnome swfdec-mozilla
```

---

### Post by stupidtrooper501 on 2010-08-05
no it did not work now it wants me gnome: Depends: epiphany-extensions but it is not going to be installed

---

### Post by Ozymandias_117 on 2010-08-05
Add it to the end ;)

---

### Post by stupidtrooper501 on 2010-08-05
like this? sudo aptitude update && sudo aptitude install gnome swfdec-mozilla + gnome epiphany-extensions

---

### Post by stupidtrooper501 on 2010-08-06
i think im going to reinstall ubuntu. good thing i have an external back up

---

### Post by Ozymandias_117 on 2010-08-06
> **stupidtrooper501 said:**
> like this? sudo aptitude update && sudo aptitude install gnome swfdec-mozilla + gnome epiphany-extensions

No. ```
sudo aptitude update && sudo aptitude install gnome swfdec-mozilla epiphany-extensions
```


I'm not sure what's up with the automatic dependency resolution... I've been having problems with it today as well.

---

### Post by stupidtrooper501 on 2010-08-07
thanks for the help but i reinstalled ubuntu instead

---

