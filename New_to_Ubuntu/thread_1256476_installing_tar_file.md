---
title: "installing tar file"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by ibbill on 2009-09-02
have downloaded a driver for a webcam to the desk top how to extract and install the driver

have included 2 pics also does allow executing this program should this be checked also.

thanks 

was told to put this in the terminal with no luck $ tar zxvf qc-usb-0.6.6.tar.gz

thanks for any help never sure what to put in the terminal

this is the site I downloaded it from [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)

---

### Post by Bachstelze on 2009-09-02
A .tar.gz file is an archive (like a .zip for example), not a program, so it can't be executed. In your case, the archive most likely contain source code that you'll have to compile, but first, you need to extract it. Do:

```
cd ~/Desktop
tar xzvf qc-usb-0.6.6.tar.gz
```

The reason it didn't work when you typed it is that the file is on your desktop, not in your home folder, so you first have to change the current directory to ~/Desktop.

---

### Post by ibbill on 2009-09-02
thank you ever so much have made a copy of the command you posted for future use.

click on it  opens and closes though there may be a way of getting around this. Old logitech camera. Time to get a new one thanks ever so much for you help.

Suggestion for the type of webcam I should buy for ubuntu as I will never need it for windows again wheeeeeeeeeee.



Bill

---

### Post by lkraemer on 2009-09-02
Bill,
Now that you have the file extracted, you should have a folder named
something like this: qc-usb-0.6.6

Compiling the source should then be a case of simply of cd-ing to the new qc-usb-X.XX directory and executing the following command:
```

cd ./qc-usb-0.6.6
make all

```
After a few moments the compiler will produce a loadable kernel module (LKM) named quickcam.ko for kernel 2.6.x or quickcam.o for kernel 2.4.x.

If the USB and V4L modules are already loaded, then you can load the module by typing one of the following commands (as root). For a 2.6.x kernel:
```

sudo insmod ./quickcam.ko

```
Or, for kernel 2.4.x:
```

sudo insmod ./quickcam.o

```
Once the quickcam module has been successfully loaded, it is time to fire up your favorite V4L application to start viewing pictures from the webcam.

At least that is what the directions are stating.

lkraemer

---

### Post by ibbill on 2009-09-03
lkraemer thanks for your help.

 Darn I gave the webcam to my neighbour here in the senior building. Installed it for her on her xp.  ouch

Would have really liked  to use your installation instructions. Thanks again for your help. 

Note have read some of the logitech forums not sure they are much help with linux systems or care to be of any help.

May look around for another type of webcam.

Thanks again for your help.

---

### Post by MelDJ on 2009-09-03
hi there maybe you could be interested in this: [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually")

---

### Post by ibbill on 2009-09-03
Awesome thanks very much can also pass this on to my 2 kids and son in law that are slowly switching over to ubuntu also.

---

