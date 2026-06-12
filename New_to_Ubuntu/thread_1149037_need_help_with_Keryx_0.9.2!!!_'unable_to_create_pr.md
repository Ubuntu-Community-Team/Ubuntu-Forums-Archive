---
title: "need help with Keryx 0.9.2!!! 'unable to create project'!!!"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by sstewart207 on 2009-05-04
okay so I've been having trouble setting up my internet connection with ubuntu. and i downloaded the drivers and the dependencies manually from packages.ubuntu.com. then some error popped up that i had broken dependencies or something like that, and now im trying to use Keryx 0.9.2  to download the dependenices and i follow the instructions that came with the program and it says open a terminal and navigate top the directory of the linux folder. so i finally found out i had to cd into the folder by going cd python keryx.py --create <project name>. where project name was my name cause i couldnt think of anything lol. and then terminal said unable to create project!!!

 i really need my internet working but first it said fix the broken dependencies first sooo yeah i need HELP!!!!!!!

btw i am running ubuntu 8.04 
bye

---

### Post by sstewart207 on 2009-05-04
cccaaaannnn sooommmeeeooonnnneeeee heeeellllppppp meeeeeeee????????

---

### Post by EXCiD3 on 2009-05-04
First you have to cd to the directory such as

```
cd /media/disk/keryx-0.92
```

then you create the project

```
python keryx.py --create project debian
```

are you sure you are creating the project using "python keryx.py --create <projectname> debian" in the correct folder? You need to specify the plugin named "debian" in order for it to work. Some knowledge of the terminal is required for now. 

If you install these 4 packages, you can use the graphical interface for Keryx to create a project without having to do it with the terminal: python-wxversion, python-wxgtk2.8, libwxgtk2.8-0, libwxbase2.8-0. It would be another trip to some place with internet for you but you wouldn't have to learn the terminal commands to change directories. I highly suggest you do learn the terminal if you plan on using linux in the future though.

---

### Post by sstewart207 on 2009-05-04
yeah i already tried that from a link you posted earlier. :'(

---

### Post by dkruidhof on 2009-05-04
I had to run it as super user to get access to write the files. so that would be: ```
sudo python keryx.py --create project debian
``` 
That's because the way my usb drive was mounted. I don't know if write access is the problem for you though.

---

### Post by EXCiD3 on 2009-05-04
It could be that you were not root. I did not have to be root because I have Gnome automount for me.

sstewart207, can you provide me with every step you did from start to finish? I am the developer of Keryx so there shouldn't be anything I can't help you with. :)

---

### Post by sstewart207 on 2009-05-05
> **EXCiD3 said:**
> First you have to cd to the directory such as

```
cd /media/disk/keryx-0.92
```

then you create the project

```
python keryx.py --create project debian
```

are you sure you are creating the project using "python keryx.py --create <projectname> debian" in the correct folder? You need to specify the plugin named "debian" in order for it to work. Some knowledge of the terminal is required for now. 

If you install these 4 packages, you can use the graphical interface for Keryx to create a project without having to do it with the terminal: python-wxversion, python-wxgtk2.8, libwxgtk2.8-0, libwxbase2.8-0. It would be another trip to some place with internet for you but you wouldn't have to learn the terminal commands to change directories. I highly suggest you do learn the terminal if you plan on using linux in the future though.

thanks for your help. i will try that when i get home today :)

:guitar:

---

