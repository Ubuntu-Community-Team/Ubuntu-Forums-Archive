---
title: "how do i check if a program is running and if not ?"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by joesto1 on 2011-01-24
hi all
i have a program called teamviewer and would like to how to check if it working and if not to restart it and tips would be magic
thanks

i am running 10.4
joe
:popcorn:

---

### Post by Claus7 on 2011-01-24
Hello,

in order to see all your programs running just type:
```
ps ux
```

if your program in question is active, you will find it there!

Regards!

---

### Post by cek on 2011-01-24
The terminal command ps will list all running programs.  To get running program info, I usually use the following (in a Terminal obviously):

```
ps -ef | grep <program name>
```

---

### Post by nick_goodfate on 2011-01-24
Or graphically System>Administration>System Monitor, "processes" tab.

---

### Post by joesto1 on 2011-01-24
thanks for the swift replys all good and helpfull

thanks cef
ps -ef | grep <program name>
this looks like i am on the way 
so i stopped teamviewer from running and got just 
3726  3708  0 19:29 pts/2    00:00:00 grep --color=auto teamviewer                       good

i started teamviewer and got
/opt/teamviewer/teamviewer/5/wine/bin/wineserver                                                   good 
so if i write a script would i just put the file location in to run it?
thanks
joe:popcorn:

---

