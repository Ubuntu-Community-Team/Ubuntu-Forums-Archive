---
title: "Removing Handbrake"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by kilroy423 on 2009-09-04
Hey everyone,

I'm trying to remove HandBrake svn1849.  I have looked in synaptics, dpkg(dpkg -l and dpkg --get-selections), tried to run make uninstall, however all attempts failed.  Does anyone know how to remove Handbrake?

Thanks,

Kilroy

---

### Post by NoaHall on 2009-09-04
try "sudo apt-get remove --purge handbrake"

---

### Post by kilroy423 on 2009-09-04
handbrake wasn't installed using apt-get, but compiled.  So to the best of my knowledge it won't be in the apt database.  I have also searched though apt-cache to see if that would work(apt-cache search ghb and handbrake come back with nothing.

```

dan@Laptop:~/Desktop/HandBrake-0.9.3$ sudo apt-get remove --purge handbrake
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package handbrake

```

Thanks,

Kilroy

---

### Post by NoaHall on 2009-09-04
I know it was complied - but sometimes with system updates, they can be added to apt-get ;)
Are you sure it's even still installed? Maybe the links are just still there. Try running "sudo ldconfig" then "sudo make uninstall" again

---

### Post by oldos2er on 2009-09-04
If you installed it with "sudo make install", you'll need to go back to the source code folder and enter "sudo make uninstall".

---

### Post by kilroy423 on 2009-09-04
> I know it was complied - but sometimes with system updates, they can be added to apt-get

my bad

> If you installed it with "sudo make install", you'll need to go back to the source code folder and enter "sudo make uninstall". 

unfortunately there is no uninstall rule :(

make uninstall
make: *** No rule to make target `uninstall'.  Stop

Thanks

---

### Post by oldos2er on 2009-09-04
> **kilroy423 said:**
> my bad



unfortunately there is no uninstall rule :(

make uninstall
make: *** No rule to make target `uninstall'.  Stop

Thanks

 You need to run that command from the folder where the code was compiled.

---

### Post by kilroy423 on 2009-09-04
> You need to run that command from the folder where the code was compiled. 


Gah!  I must have deleted that folder.  How about the command to check out a certain revision from svn?

---

### Post by NoaHall on 2009-09-04
You mean you were just running it from default terminal location? XD Okay then. XD I suppose, you could download, install(so it replaces the version you have), and then do "sudo make uninstall"

---

### Post by kilroy423 on 2009-09-04
I just checked the old version out from svn.  I'm going to try and do make uninstall with it.  Wish me luck.

FYI command for checking out an old svn version is where -r is the revision

```
svn co -r 1849 svn://svn.handbrake.fr/HandBrake/trunk HandBrake
```

---

