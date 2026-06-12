---
title: "what is the proper way of uninstall an application on the terminal?"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-14
what is the proper way of uninstall an application on the terminal?

apt-get remove app-*
doesnt work

the system doesnt recognize the app since it is installed in /opt directory.

cd /opt
ls -al
rm -r app

is there a better way, or would that work?

---

### Post by 3rdalbum on 2011-08-14
Follow the instructions that came with the program. If there are no instructions, then sure, just delete the files associated with it that aren't associated with anything else.

---

### Post by hakermania on 2011-08-14
Be sure to use the 'locate' command to find all the associated files

---

### Post by kimda on 2011-08-14
How did you install this program? Is it a source package? Sometimes you can do a make uninstall in the folder you made the program. 
If it is a deb file you installed you can remove it with dpkg. 
ex.  dpkg -r packagename 
You can  also remove this program with synaptic. You can find the package with the following command: dpkg -l | grep package

---

### Post by 007casper on 2011-08-14
@hakermania
what is the full command.

locate app 

?

@kimda
I installed latest nginx to opt directory from source distribution.  Then, realized that I can install it from ubuntu package through apt-get install nginx.

So, I would like to delete the nginx files in opt directory. 

I did use

make 
make install

---

### Post by babakott on 2011-08-14
You should be able to cd into the source directory and type
```
make uninstall
```

---

### Post by kimda on 2011-08-14
Next time if you find a program you want to install search first in the Ubuntu repos. If its not in the repos it could be in a ppa repo (lots of developers have their own ppa repos). Installing packages from source can cause serious headaches. They are not always easy to uninstall and you can even mess up your system. I try to avoid installing from source as much as possible.

---

### Post by 007casper on 2011-08-14
cd /opt
ls -al
nginx
nginx-1.0.0

root@server:/opt# make uninstall nginx-1.0.0
make: *** No rule to make target `uninstall'.  Stop.
root@server:/opt# make uninstall
make: *** No rule to make target `uninstall'.  Stop.

?

---

### Post by 007casper on 2011-08-15
bump

---

