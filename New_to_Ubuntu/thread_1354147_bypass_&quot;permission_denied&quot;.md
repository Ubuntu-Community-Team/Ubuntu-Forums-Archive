---
title: "bypass &quot;permission denied&quot;"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by diosilva16 on 2009-12-13
i'm following this tutorial [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html) to instal a tablet on my sistem, but when i get to the part that says 
"Create a new file with the name /etc/hal/fdi/policy/99-x11-wizardpen.fdi"
i get stuck, because when i try to create a new file in the folder it gives me a permission denied message, i think i should use the terminal and the sudo comand, but i don't know how to create and edit files in the terminal

---

### Post by Physical Hook on 2009-12-13
```
sudo touch /etc/hal/fdi/policy/99-x11-wizardpen.fdi # create an empty file
gksudo gedit /etc/hal/fdi/policy/99-x11-wizardpen.fdi # open Gedit and edit it
``````
gksudo nautilus /etc/hal/fdi/policy # open Nautilus with root privileges
```

---

### Post by SuperSonic4 on 2009-12-13
You do need to use sudo.

```
sudo touch /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```

You can edit on the CLI using ```
sudo nano /etc/hal/fdi/policy/99-x11-wizardpen.fdi
``` 

or ```
gksu gedit /etc/hal/fdi/policy/99-x11-wizardpen.fdi
``` for a CLI

---

### Post by diosilva16 on 2009-12-13
thanks a lot for the help and for the speed of the replies, guys

---

