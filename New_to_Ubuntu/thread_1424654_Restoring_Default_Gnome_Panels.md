---
title: "Restoring Default Gnome Panels"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by Maxcore on 2010-03-08
Hello. I have been using Ubuntu for a year now (moderate usage) and have changed my gnome panels over this time period. I recently decided I like the default layout much more and was wondering if there is an easy way to set gnome back to the default panels. Any help would be great, thanks.

---

### Post by NightwishFan on 2010-03-08
Run this in the terminal.
```
gconftool2 --recursive-unset /apps/panel
```

---

### Post by Maxcore on 2010-03-08
Oh cool. All my panels are gone though, so is there a way to create new ones from the command line?

---

### Post by Maxcore on 2010-03-08
Wow, I just realized that this really sucks. I don't know how to launch any of my applications without using the menu bar. I tried creating a launcher on my desktop to "bash" but nothing happens when I run it. I also tried creating a launching to gnome-panel but nothing happened when I ran that as well. What should I do?

---

### Post by NightwishFan on 2010-03-08
It is just new for you. Just open the terminal under Applications -> Accessories.

Try logging out and back in, if that does not work, I will get back to you.

---

### Post by MichealH on 2010-03-08
> **Maxcore said:**
> Oh cool. All my panels are gone though, so is there a way to create new ones from the command line?

> **Maxcore said:**
> Wow, I just realized that this really sucks. I don't know how to launch any of my applications without using the menu bar. I tried creating a launcher on my desktop to "bash" but nothing happens when I run it. I also tried creating a launching to gnome-panel but nothing happened when I ran that as well. What should I do?

ALT+F2
Type in:
```
gnome-terminal
```
Then do what NightwishFan said :D

Which was:
> **NightwishFan said:**
> Run this in the terminal.
```
gconftool2 --recursive-unset /apps/panel
```

---

### Post by Maxcore on 2010-03-08
I ran the command in the terminal and it destroyed all of my panels so I couldn't click "Applications -> Accessories -> Terminal". What I ended up doing was running "gnome-panel" (which did nothing originally) and then running "gnome-command-center" and using that to start the task manager and killing gnome-panel which made all of the default panels come back. Thanks guys.

---

### Post by MichealH on 2010-03-08
> **Maxcore said:**
> I ran the command in the terminal and it destroyed all of my panels so I couldn't click "Applications -> Accessories -> Terminal". What I ended up doing was running "gnome-panel" (which did nothing originally) and then running "gnome-command-center" and using that to start the task manager and killing gnome-panel which made all of the default panels come back. Thanks guys.

Glad It worked out in the end :D

Mark this thread as [SOLVED] It will help others find the answer better. Goto Thread Tools> Mark thread as SOLVED

Thanks 
MichealH

---

### Post by lpugz48 on 2012-08-17
Thanks, that worked great. Had to leave out the "2" for it to work.

---

