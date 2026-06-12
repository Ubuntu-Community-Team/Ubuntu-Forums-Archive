---
title: "directory write permission"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by beelzebufo on 2010-06-25
I am getting this error message what do I need to do?   "launcher requires write permission to the c:\program files\world of warcraft trial directory to successfully patch the game. please enable write access to the directory using an administrator account"  my user account is as admin. so I confused...  I already had this installed at one point yesterday, and uninstalled because of a deficiency in wine, but wanted to try fiddling with it again to see if I can get it going

---

### Post by Drenriza on 2010-06-25
say

```
sudo chmod -R 755 /home/your-user-name/.wine/drive_c/Program\ Files/world\ of\ warcraft 
```
example
```
sudo chmod -R 755 /home/cristian/.wine/drive_c/Program\ Files/world\ of\ warcraft 
```
```
sudo chmod -R 755 /home/Sofie/.wine/drive_c/Program\ Files/world\ of\ warcraft 
```

---

### Post by beelzebufo on 2010-06-25
ugh... again, as always, no such file or directory.  I copied and pasted your code (with my user name of course)  so complicated on linux!!!!!!!!!!! aaaarrrrrrgggggghhhhhh!  why would I not have write authority on any directory other than root or boot and sys. files? and why did it install before, and now it wont reinstall?

---

### Post by 3rdalbum on 2010-06-25
> **beelzebufo said:**
> ugh... again, as always, no such file or directory.  I copied and pasted your code (with my user name of course)  so complicated on linux!!!!!!!!!!! aaaarrrrrrgggggghhhhhh!  why would I not have write authority on any directory other than root or boot and sys. files?
You   have   write   access   to   your   home   directory   already.   The   error   message   that   the   Windows   program   is   showing   you   is   inaccurate   because   as   far   as  the  program  is  concerned,   your   '.wine'  directory  in  your  home  directory   is  all   that  exists.

Try   searching  for   that   error   message  and  the  word   'wine'  on  Google.

---

### Post by Drenriza on 2010-06-25
try navigate to the warcraft file inside of wine

start here if possible
```
/home/username/.wine
```
and then with cd navigate to the warcraft file, use
```
pwd
```

and if you need help adjusting the command, type the output of pwd here.

---

### Post by mimiteto on 2010-06-25
Open some console (Alt + F2 >> xterm) and then use  ```
 chmod 777 .wine 
``` I hope we helped you :p

---

### Post by Drenriza on 2010-06-25
> **mimiteto said:**
> Open some console (Alt + F2 >> xterm) and then use  " chmod 777 .wine " I hope we helped you :p

```
sudo chmod -R 777 /home/username/.wine
```
Give it a try.

---

### Post by iponeverything on 2010-06-25
it is not complex:

```
gksu nautilus
```

Go to your .wine folder right click on it and go to properties.

---

### Post by tarps87 on 2010-06-25
> **Drenriza said:**
> say

```
sudo chmod -R 755 /home/your-user-name/.wine/drive_c/Program\ Files/world\ of\ warcraft 
```
example
```
sudo chmod -R 755 /home/cristian/.wine/drive_c/Program\ Files/world\ of\ warcraft 
```
```
sudo chmod -R 755 /home/Sofie/.wine/drive_c/Program\ Files/world\ of\ warcraft 
```

> **Drenriza said:**
> ```
sudo chmod -R 777 /home/username/.wine
```
Give it a try.

Just a note, to save complication with the users home directory you can use ~
e.g.
```
sudo chmod -R 777 /home/username/.wine
```
```
sudo chmod -R 777 ~/.wine
```
Most users log in as themselves (what with root disabled by default)

---

### Post by beelzebufo on 2010-06-25
thank you guys! I just checked this thread and haven't had a chance to try any of this yet, but i'm sure something will work

thanks again

---

### Post by altjx on 2010-07-25
> **tarps87 said:**
> Just a note, to save complication with the users home directory you can use ~
e.g.
```
sudo chmod -R 777 /home/username/.wine
```
```
sudo chmod -R 777 ~/.wine
```
Most users log in as themselves (what with root disabled by default)

Didn't work for me. Tried 777 and 755 like above post. Neither worked. Still getting same message. Any other suggestions?

---

### Post by altjx on 2010-07-25
Nvm. Although I got the error, I was able to hit the Play button and it went through.

---

