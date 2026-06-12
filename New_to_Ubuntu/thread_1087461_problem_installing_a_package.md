---
title: "problem installing a package"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by minaesm on 2009-03-05
hi 
i want to install apackage i did this 
>cd Desktop
>sudo tar -xvf hdf5-1.6.8.tar.gz
>cd hdf5-1.6.8
but at this point i have to change a line in one of the files of hdf5 directory and then install it but there is a picture of a lock on the folder and whenever i want to save the changes it says that i don't have permission to do so . what should i do to remove that lock and have permission to make changes in those files ???

---

### Post by taurus on 2009-03-05
If you unpack the file in your own $HOME, you do not have to use sudo.  Only use sudo when you get to the last step, installing it to your system.

```
cd ~/Destop
sudo rm -rf hdf5-1.6.8
tar xvzf hdf5-1.6.8.tar.gz
cd hdf5-1.6.8
```

---

### Post by Bölvaður on 2009-03-05
oh yeah. If I get this right you got a .tar.gz archive on your desktop. So that will make everything you did correct EXCEPT:


$**sudo **tar -xvf hdf5-1.6.8.tar.gz

do not use sudo. That means you just un tar-ed the archive with the super user (root) which now owns the file.. not you. Everyone that has super user privileges can change(damage) the system so avoid using sudo unless if you are doing system maintenance. 

just do the same thing again without the sudo.
and you do not need to install programs with sudo from tar.gz files. It may be safer just to keep them in your home directory (/home/you/programs/) so they cannot change your system :)

---

