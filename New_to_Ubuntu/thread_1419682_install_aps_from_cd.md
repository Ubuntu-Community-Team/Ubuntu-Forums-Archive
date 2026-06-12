---
title: "install aps from cd"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by mbzn on 2010-03-02
Hi i'm running 9.10 and has a iso with '9.10 and alot of apps' on it, the iso is the standard 9.10 with games and and and. I could write the iso to a disk and reinstall but this would make me have to start from scratch(video drivers etc.) the reason i want to install from the cd is that my internet is expensive. 
So, how can i list the apps on the disc and install them?

Thanx in advance

---

### Post by dragonboss on 2010-03-02
Install AptOnCD and it will make and iso of currently installed packages so you can burn it and then install from cd.
Code: sudo apt-get install aptoncd. Or search for it in the Ubuntu Software Center

---

### Post by mbzn on 2010-03-02
Thanks for the reply
This will create a iso of my current install, am i right?

If i am then i would still have the other iso with the packages i want on it...

So i have a fully functional system 9.10, without package 'X' but with packages 'Y and Z'
And i have a iso(bootable live cd of 9.10) with package 'X' but without packages 'Y and Z'(which i also need)
So i want to install package 'X' from the iso

Sorry if this wasn't clear

---

### Post by juancarlospaco on 2010-03-02
[**Follow the rabbit**]("http://ubuntuforums.org/showthread.php?t=352460&highlight=repo+dvd")

---

### Post by dragonboss on 2010-03-02
You can install package X by installing aptoncd on the machine without package X and then pop in the cd and select restore from the aptoncd.

---

### Post by mbzn on 2010-03-02
Ok, so APTonCD is going to work, how do i load an iso? or do i have to write it to disk?

---

### Post by juancarlospaco on 2010-03-02
Right click menu over an .iso file gives you an option to Mount the iso.

---

### Post by mbzn on 2010-03-02
But APTonCD only checks my CD-rom's and i cant see an option to direct it to the mounted iso.

Thanks anyway

---

### Post by dragonboss on 2010-03-02
Then you would have to burn the iso to disk to use it.

---

### Post by mbzn on 2010-03-02
Ok i found it. If you click the load button it takes an iso (i went file>Add)

Thanks again for all the advice..

---

### Post by Pritamsng on 2010-03-02
some extra thing you can do by creating repository..
check the link...

[http://linuximagination.blogspot.com/2009/12/configure-ubuntu-repository.html](http://linuximagination.blogspot.com/2009/12/configure-ubuntu-repository.html)

---

