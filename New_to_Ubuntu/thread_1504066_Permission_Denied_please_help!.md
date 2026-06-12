---
title: "Permission Denied please help!"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by denis153 on 2010-06-07
Okay So I am trying to move a 2 files one named lc002182.htm and pbsetup.run into the directorie of:

the file lc002182.htm needs to go here
usr>local>games>armyops>system>pb>htm


and the pbsetup.run needs to go to:
usr>local>games>armyops>system>pb
but everytime i try and do that it says permission denied!
PLease help!

---

### Post by Breambutt on 2010-06-07
Navigate into the folder where those files are and copypasta in terminal

```
sudo mv lc002182.htm /usr/local/games/armyops/system/pb/htm/
sudo mv pbsetup.run /usr/local/games/armyops/system/pb/
```

Permission denied = put *sudo* in front of the command

Or alternatively *gksu nautilus* to enter the file manager with sufficient permissions.

---

### Post by kaldor on 2010-06-07
That's right; *sudo* lets you run any command as if you were Root (administrator).

---

### Post by Mariane on 2010-06-07
Open a terminal window in the directory where your files are. 

Type:
sudo mv lc002182.htm /usr/local/games/armyops/system/pb/htm/lc002182.htm

and 

sudo mv pbsetup.run /usr/local/games/armyops/system/pb/pbsetup.run

Enter your root password if prompted. 

Mariane

---

### Post by denis153 on 2010-06-07
Breambutt and Mariane thank you so much! Nobody ever helped me so quickly~!
:KS

---

