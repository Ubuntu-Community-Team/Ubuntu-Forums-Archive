---
title: "Avg 7.5 Linux Version Help"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by linuxmann on 2007-04-22
i just got a disk from grisoft two days ago and tried to install it today. it says i have to extract the tar.gz file (not to a specific location) and run the install.sh file to install it. I tried to install it from Konsole and this is the message i receved. 

jolly@jolly-desktop:~$ /home/jolly/Desktop/avg7-linux/install.sh
File: 'script/print_message.sh' was not found. Installation aborted.
jolly@jolly-desktop:~$

it says it cannot find the print message.sh file. But when i went to the script folder in the avg7-linux folder the print_message.sh was there.

Is there anyway i can unlock root without it saying permission denied in Konsole or anywhere else.

if you need anymore details i will try to provide more.

---

### Post by bswilson on 2007-04-22
> **linuxmann said:**
> jolly@jolly-desktop:~$ /home/jolly/Desktop/avg7-linux/install.sh
File: 'script/print_message.sh' was not found. Installation aborted.
jolly@jolly-desktop:~$

it says it cannot find the print message.sh file. But when i went to the script folder in the avg7-linux folder the print_message.sh was there.

Did you run the installer script by using **sudo**, or did you only execute it as yourself?

---

### Post by linuxmann on 2007-04-22
I tried sudo but it still says this.  

jolly@jolly-desktop:~$ sudo /home/jolly/Desktop/avg7-linux/install.sh
Password:
File: 'script/print_message.sh' was not found. Installation aborted.
jolly@jolly-desktop:~$


i will provide screenshots to have better clarification.

When i copied the directory plus the install (not shown)
[http://img214.imageshack.us/my.php?image=avg75yz7.png](http://img214.imageshack.us/my.php?image=avg75yz7.png)

The print_message.sh is there
[http://img214.imageshack.us/my.php?image=printmessagewl9.png](http://img214.imageshack.us/my.php?image=printmessagewl9.png)

The install.sh
[http://img214.imageshack.us/my.php?image=avgml8.png](http://img214.imageshack.us/my.php?image=avgml8.png)

This is when i use the sudo pasword with the command. Notice it says print_message.sh is not found. Thats where i need help.
[http://img214.imageshack.us/my.php?image=passwordch9.png](http://img214.imageshack.us/my.php?image=passwordch9.png)

---

### Post by go_beep_yourself on 2007-11-21
Has anyone had this problem?

[http://img214.imageshack.us/img214/5953/screenshotavgforlinuxwoco2.png](http://img214.imageshack.us/img214/5953/screenshotavgforlinuxwoco2.png)

---

