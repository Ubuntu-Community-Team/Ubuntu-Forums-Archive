---
title: "folder ownership"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by vlad1975 on 2009-10-03
Hello


I just transfered copy a file from my friends HDD to my HDd and im getting error saying the i am not the owner of the folder

please see screenshot


could someone guide me on how i can change this please? what command i need to run?

---

### Post by cogier on 2009-10-03
Hi,

I found this link that should help.

[http://ubuntuforums.org/showthread.php?t=278718]("http://ubuntuforums.org/showthread.php?t=278718")

---

### Post by nothingspecial on 2009-10-03
```
sudo chown username:username /path/to/file
```

---

### Post by vlad1975 on 2009-10-03
Hello i tried that

ed@ed-desktop:~$ sudo chown username:ed /media/LaCie/Andromeda
[sudo] password for ed: 
chown: invalid user: `username:ed'
ed@ed-desktop:~$ sudo chown username: /media/LaCie/Andromeda

i am assuming im putting the username and password when i log in ubuntu but i get this error

---

### Post by nothingspecial on 2009-10-03
> **vlad1975 said:**
> Hello i tried that

ed@ed-desktop:~$ sudo chown username:ed /media/LaCie/Andromeda
[sudo] password for ed: 
chown: invalid user: `username:ed'
ed@ed-desktop:~$ sudo chown username: /media/LaCie/Andromeda

i am assuming im putting the username and password when i log in ubuntu but i get this error
```

sudo chown ed:ed /media/LaCie/Andromeda
```

first one is the user owner second one is group.

---

### Post by nothingspecial on 2009-10-03
If Andromeda is a directory rather than a file you will need the R flag to change the ownership of everything inside it
```

sudo chown -R ed:ed /media/LaCie/Andromeda/
```

---

### Post by vlad1975 on 2009-10-03
oh ok 


so when i run that is there anything else i need to do?

ed@ed-desktop:~$ sudo chown ed:ed /media/LaCie/Andromeda
ed@ed-desktop:~$ 
 coz this is what i get and when i check the permission it still shows same as screenshot

---

### Post by nothingspecial on 2009-10-03
It depends what file system your external drive has.

The ones that don`t support unix file permissions will tell you that root owns the file even if it doesn`t. Maybe you need to change the permissions. If you don`t mind any user being able to delete etc Andromeda then
```

 chmod 777 /media/LaCie/Andromeda
```

you might need a sudo although after the last command you should own it and not need one.

Read [[COLOR="Magenta"]this[/COLOR]]("http://linuxcommand.org/lts0070.php")

---

### Post by djchandler on 2009-10-03
I'll probably get flamed for telling you this, but you can get root privileges in Nautilus if the command line thing is making you uncomfortable. I see a lot of code but no results for the user , so here goes.

Hit key combination "**Alt-F2**"

When the dialog pops up, enter: **gksu nautilus**

Enter your administrative **password**

navigate to the folder in question (you'll be starting in /home/root) and right click, scroll down to "**properties**" and left click

click on  the **Permissions** tab

use drop-downs under **owner** and **group** and change to your main log-in name and group

Make sure you exit nautilus when done. reopen as your regular account and see if you have access.

You should be good to go.

---

### Post by nothingspecial on 2009-10-03
> **djchandler said:**
> I'll probably get flamed for telling you this, 

Don`t see why you should. Anything that get`s the job done ;)

---

### Post by djchandler on 2009-10-03
Thanks for my Daily Affirmation. 

I wonder if Al Franken does those in the U.S. Senate now. ;)

Let's hope between the two or so of us that Vlad1975 has solved his conundrum.

---

### Post by user333 on 2009-10-03
I do it this way, instead of writing :

sudo chown ed.ed /media/LaCie/Andromeda, 

I always to this(I will put the exact commands for you to write):

cd /media
cd LaCie
sudo chown -R ed.ed Andromeda

This has always worked for me, even If it is a system folder of file. (but that is dangerous, I only use it if I have to)

---

