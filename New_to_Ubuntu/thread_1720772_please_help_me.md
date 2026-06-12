---
title: "please help me"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by ubunt12 on 2011-04-03
hi, i have these commands that i would like to execute on system startup:
```

sudo echo "0" /proc/sys/kernel/randomize_va_space
sudo echo "0" /proc/sys/kerenl/exec-shield
sudo echo "1" /proc/sys/net/ipv4/ip_forward

```if anyone could take me through the steps as to which file to add these commands so they will exec
on sys startup it would be most appreciated.
Thanks.

---

### Post by KL_72_TR on 2011-04-03
This is not the answer you're looking but I think it will back you up in the future. Go to the link and download the PDF
[http://sourceforge.net/projects/linuxcommand/](http://sourceforge.net/projects/linuxcommand/)

---

### Post by ubunt12 on 2011-04-03
kk thanks

---

### Post by TeoBigusGeekus on 2011-04-03
Create a file and name it my_script.
Put these lines in it
```
echo "0" /proc/sys/kernel/randomize_va_space
echo "0" /proc/sys/kerenl/exec-shield
echo "1" /proc/sys/net/ipv4/ip_forward
exit 0
```
Save it in your home folder.
Open a terminal and make it executable
```
chmod +x ~/my_script
```
From the terminal, give
```
gksu gedit /etc/rc.local
```
and add this line to the file
```
bash ~/myscript
```
Save, exit, reboot, post back.

---

### Post by ubunt12 on 2011-04-03
thanks, would that be:
```

#!/bin/bash

```
at the top of the created file??

---

### Post by TeoBigusGeekus on 2011-04-03
> **ubunt12 said:**
> thanks, would that be:
```

#!/bin/bash

```
at the top of the created file??

Yep.
Sorry, I forgot it.

---

### Post by ubunt12 on 2011-04-03
nope, it didn't seem to work thanks anyway

---

### Post by TeoBigusGeekus on 2011-04-03
Ok, check [this]("http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") out then.

---

### Post by ubunt12 on 2011-04-03
thanks for the link and sorry for wasting your time

---

### Post by TeoBigusGeekus on 2011-04-03
> **ubunt12 said:**
> thanks for the link and sorry for wasting your time

Don't say this again :popcorn:

Just post back with your progress...

EDIT: Solved!!! Brilliant...

---

