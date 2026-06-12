---
title: "Help plz: Creating Scripts in Intrepid Ibex"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by wickedcultgod on 2009-02-12
Hi. I am a new Ubuntu Itrepid Ibex user. I am trying to create a script so that my wifi works when it comes back from sleep. I got a guide that says this:

Quote:Now you should create a script to restart the interface on awake from suspend mode, as it will otherwise hang. As root, create /etc/pm/sleep.d/00wireless:

I know how to modify the script and I found the folder /etc/pm/sleep.d , but I don't know how to create a script called 00wireless. Any advice would be appreciated.  Ubuntu rocks!

---

### Post by cerealtx on 2009-02-12
maybe if u posted the guid i could be more helpfull but from terminal you could type ```
gedit /etc/pm/sleep.d/00wireless
``` and it would create that file, but im not sure what extension it should have example : .config . sh .txt

---

### Post by niteshifter on 2009-02-12
Hi,

Close ... but /etc and everything below is owned by root so make that
```
gksu gedit /etc/pm/sleep.d/00wireless.sh
```
otherwise it won't work.

I'm also guessing at the extension .sh - post a link to the guide and/or the text you're following so we can help you better, without guesswork ;)

---

### Post by lykwydchykyn on 2009-02-12
You don't need a file extension.  File extensions are purely optional in Linux; I would recommend naming it as the guide recommends.

Please post a link to the guide you are following if you need more help.

---

### Post by Predrag on 2009-02-12
Hi there is very simple solution. go to terminal and type:gksu nautilus /etc/pm/config.d  and there create file "config" open this file and add this SUSPEND_MODULES="$SUSPEND_MODULES ath_pci" .save it .tested on ubuntu 8.10 beacuse i had the same problem.another solution  :1.open terminal: cd /etc/acpi/resume.d
2. than type in terminal: gedit script.sh > add this in script.sh :

#!/bin/sh

#Restart networking
/etc/init.d/networking restart

3.chmod +x ./skript.sh

4.that`s all

---

