---
title: "php file not found"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by kapi on 2009-02-14
hi am using geany to write my first php page, try to save it to var/www and it doesnt appear. 

could someone please help

thanks

Kapi

---

### Post by hyper_ch on 2009-02-14
because your normal user does not have write access to that folder.

---

### Post by llamabr on 2009-02-14
Hi.  What editor are you using?  And where are you writing it?  Be a bit more explicit, and we can help you find out where the file is.

For starters, though, you'll want to cd to that directory:

$>cd /var/www/

then using sudo, open an editor, like nano:

$>nano first.php

Then, saving it will pop it in the right directory.  I think maybe your issue is permissions.  Did you type sudo before your command?

---

### Post by kapi on 2009-02-14
no I didnt use sudo, I just assumed I could write to the folder using save as and then naming the file. This is kind of new to me, so what am I supposed to do?

Thanks for your patience

Kapi

---

### Post by hyper_ch on 2009-02-14
kapi: simplest thing would be to give you write access to the www folder:

```

sudo chown -R USERNAME.www-data /var/www

```

where USERNAME is your username. However that is only recommended if it's a local development machine.

---

### Post by geirha on 2009-02-14
Make yourself the owner of /var/www/ and you'll be able to save files there. You can do this graphically by running nautilus with root privileges. You can do that by installing [nautilus-gksu](apt:nautilus-gksu), browse to / (Filesystem in the left-margin) then right click "var" and choose "Open as Administrator". Or, if you don't install nautilus-gksu, hit Alt+F2 to get the run-dialog, run "gksu nautilus", then browse to /var (Filesystem in left margin -> var). 

Right-click "www", select properties, go to the permissions tab, and set your user as the owner.

In the terminal you can type the following command to achieve the same:
```
sudo chown $USER /var/www
```

---

### Post by kapi on 2009-02-14
Ok installed nautilus gksu as suggested but when right click Var no such administration option appears

am I doing something wrong?

---

### Post by geirha on 2009-02-14
Sorry, nautilus needs to be restarted so that extension get's loaded, forgot to mention that. Either log out and log back in, or run in a terminal: ```
killall nautilus
``` that command will kill all currently running instances of nautilus. Nautilus is btw the program responsible of drawing the background image and the icons on the desktop, so they may disappear for a little while. Gnome will detect that nautilus has been killed, and will automatically start it again.

---

### Post by kapi on 2009-02-14
thankyou so much, next after changing the permissions I tried to open the php file in fire fox and it doesnt seem to work. Feel like a right pleb 

what have I missed out

Kapi

---

### Post by hyper_ch on 2009-02-14
what happened when you tried to open it?

---

### Post by llamabr on 2009-02-14
Easier to use sudo, than to go around changing permissions of a system wide folder.

Since you didn't have write permissions to the folder, you have to use sudo, which grants you administrator priveleges.  Since it's a system wide folder, regular users can't write to it.

Look at:

$>man sudo

for details.

---

### Post by kapi on 2009-02-14
i right click open with firefox then a pop up appears and says save as or open with?

---

### Post by hyper_ch on 2009-02-14
> **llamabr said:**
> Easier to use sudo, than to go around changing permissions of a system wide folder.

depends... on a local machine if you want to develop files sudo is too encumbering... better to chown there or give according permissions to world ;)

---

### Post by geirha on 2009-02-14
> **kapi said:**
> i right click open with firefox then a pop up appears and says save as or open with?

No, you want to open the file through apache. Apache is listening on port 80 by default, the default http port. Try opening [http://localhost/thefile.php](http://localhost/thefile.php)

---

### Post by kapi on 2009-02-16
does work after all, just rebooted the system and entered [http://localhost.test.php](http://localhost.test.php)

Thanks to everyone for your input

long live the linux revolution!

---

