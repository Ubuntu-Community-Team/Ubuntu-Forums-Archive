---
title: "File type: .pl"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by rick astley on 2009-04-14
i have a package i want to install. within the folder with the files there is one named "**install.pl**" when i right click and hit Open nothing happens. 

do i need something extra to install this type of file.

thanks,
rick.

---

### Post by N_Nick on 2009-04-14
That's a perl script.

Someone correct me if i am wrong but i dont think installing a package requires running a Perl script.

What are you trying to install?

---

### Post by achase79 on 2009-04-14
This is a perl file.  Ubuntu  installs this as a basic. You will want to run this package in terminal to see if there are any warnings you may be missing.  If it is a .deb package type ```
sudo dpkg -i
``` then drop the .deb into the terminal window (this will post the path and file to the terminal) then execute by pressing return (enter).

If this is not a .deb package run it in terminal by using the cd command to get into the directory containing install.py then running the code ```
sudo perl install.pl
```

---

### Post by rick astley on 2009-04-14
> **N_Nick said:**
> 
What are you trying to install?

im trying to install VMware Tools.

here is a list of everything in the folder after extraction:

[IMG]http://img516.imageshack.us/img516/8616/81787855.jpg[/IMG]

---

### Post by achase79 on 2009-04-14
Are you installing from the tar file?

---

### Post by N_Nick on 2009-04-14
I found this:

[http://www.ubuntugeek.com/howto-install-vmware-tools-in-ubuntu.html](http://www.ubuntugeek.com/howto-install-vmware-tools-in-ubuntu.html)

Its kinda old but it should be quite similar.

> sudo ./vmware-install.pl

You should be able to find information about installing VMware tools on google.

---

### Post by achase79 on 2009-04-14
If you are trying to install from an rpm you will at least have to convert it to a deb file using alien.  This is not recommended.  Installing from the tar file would be a better option.

---

