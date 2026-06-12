---
title: "ubuntu windows manager still wont fixxxx please help me"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by RIPwindows on 2010-10-26
hello guys i  was just tweaking my system and then removed some of those  games that  come with ubuntu so then i restart and now whenever i open a  program i  cant close resize or minimize (it does not show up). i  presume it is a problem with my windows  manager and now when i open it  from preferences this is what i get  ~Cannot start the preferences  application for your window manager
 
Window manager "gnome-screensaver" has not registered a configuration   tool~ please help me i dont wanna go and install windows 7 again. Ihave  ubuntu 10.10 hope you can help me with this problem


it also says disk mounter has not registered a configuration tool

---

### Post by stephanvaningen on 2010-10-26
Maybe you installed another window manager earlier and uninstalled it now? What happens if you type this in a terminal (Ctrl-Alt-t):
 ```
metacity --replace&
```
?

---

### Post by RIPwindows on 2010-10-26
metacity:ERROR:core/prefs.c:2495:meta_prefs_get_workspace_name: assertion failed: (workspace_names[i] != NULL) thats it :(

---

### Post by RIPwindows on 2010-10-26
> **stephanvaningen said:**
> Maybe you installed another window manager earlier and uninstalled it now? What happens if you type this in a terminal (Ctrl-Alt-t):
 ```
metacity --replace&
```?
metacity:ERROR:core/prefs.c:2495:meta_prefs_get_workspace_name: assertion failed: (workspace_names[i] != NULL) thats it

---

### Post by stephanvaningen on 2010-10-26
Ok, ...
What if you do this in terminal:
 ```
cd ~
mv ./.gconf ./.gconf.backup

```
Then logout and login again: any improvements?

---

### Post by stephanvaningen on 2010-10-26
FYI, to undo the above afterwards do:
 ```
rm -R ./.gconf
mv ./.gconf.backup ./.gconf
```
and then logout and login again...

> **stephanvaningen said:**
> Ok, ...
What if you do this in terminal:
 ```
cd ~
mv ./.gconf ./.gconf.backup

```
Then logout and login again: any improvements?

---

### Post by RIPwindows on 2010-10-26
> **stephanvaningen said:**
> FYI, to undo the above afterwards do:
 ```
rm -R ./.gconf
mv ./.gconf.backup ./.gconf
```and then logout and login again...
mv: cannot stat `./.gconf': No such file or directory

---

### Post by stephanvaningen on 2010-10-26
?  hmmm ...
*You run Ubuntu, not Kubuntu or Xubuntu?
*You get this message after the first time?
*You ran it from your home (After doing i.e. 'cd ~')?
*What does this give you?:
 ```
ls ./.gcon*
```
> **RIPwindows said:**
> mv: cannot stat `./.gconf': No such file or directory

---

### Post by RIPwindows on 2010-10-26
> **stephanvaningen said:**
> ?  hmmm ...
*You run Ubuntu, not Kubuntu or Xubuntu?
*You get this message after the first time?
*You ran it from your home (After doing i.e. 'cd ~')?
*What does this give you?:
 ```
ls ./.gcon*
```
i run ubuntu 10.10 maverick meerkat

this is what i got   ./.gconf:
apps  desktop

./.gconfd:
saved_state
peter@peter-Dimension-4700c:~$

---

### Post by stephanvaningen on 2010-10-26
Then I can assume your working directory wasn't home. Try
 ```
mv /home/peter/.gconf /home/peter/.gconf.backup
```
should do the mv without errors...
Then logout/login to verify result: ?

> **RIPwindows said:**
> i run ubuntu 10.10 

this is what i got   ./.gconf:
apps  desktop

./.gconfd:
saved_state
peter@peter-Dimension-4700c:~$

---

### Post by RIPwindows on 2010-10-26
> **stephanvaningen said:**
> Then I can assume your working directory wasn't home. Try
 ```
mv /home/peter/.gconf /home/peter/.gconf.backup
```should do the mv without errors...
Then logout/login to verify result: ?             yes finally you helped me fix it you pwn dude :) thanks a lot

---

### Post by stephanvaningen on 2010-10-26
Sorry, I'm not so good in slang-things? pwn? means everything is ok now? 

> **RIPwindows said:**
> yes finally you helped me fix it you pwn dude :) thanks a lot

---

### Post by RIPwindows on 2010-10-26
> **stephanvaningen said:**
> Then I can assume your working directory wasn't home. Try
 ```
mv /home/peter/.gconf /home/peter/.gconf.backup
```should do the mv without errors...
Then logout/login to verify result: ?


thanks it worked you pwn

---

### Post by stephanvaningen on 2010-10-26
;-)

(don't forget to mark this thread [solved])

---

