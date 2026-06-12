---
title: "Need help in ubuntu"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by navaneethan on 2009-02-25
Friends my self Navaneethan i have installed ubuntu hardy and also my friend also have installed it as well as he updated many suites   for hardy over internet.i also want to install those packages...so i searched how to install those packages without inet..i had a method that is  i copied all packages from ubuntu cache in my friend's hardy ...then copied those packages into my desktop and i typed the command "sudo dpkg -i *.deb" all packages have updated after i restart my computer then it doesn't enter into graphical login(doesn't ask user name and passwd in gui mode)..it localhost login in blank screen ...then i don't know how to solve it ..i have tried startx command it doesn't help me....but my friend's s/m configuration is different from mine.....how to solve it without reinstallation ??

---

### Post by Flyingjester on 2009-02-25
does startx give you any error messages?

---

### Post by llamabr on 2009-02-25
Packages will be often fairly specific to one computer's configuration.  You'll likely break something by just blindly copying them all over.

If your machine is not on the internet, you can make a few cd's with all of the packages you want on them, and install with apt-cdrom in much the same way you would with apt-get.

Yes, I think a reinstall is in order.

---

### Post by navaneethan on 2009-02-25
> **navaneethan said:**
> Friends my self Navaneethan i have installed ubuntu hardy and also my friend also have installed it as well as he updated many suites   for hardy over internet.i also want to install those packages...so i searched how to install those packages without inet..i had a method that is  i copied all packages from ubuntu cache in my friend's hardy ...then copied those packages into my desktop and i typed the command "sudo dpkg -i *.deb" all packages have updated after i restart my computer then it doesn't enter into graphical login(doesn't ask user name and passwd in gui mode)..it localhost login in blank screen ...then i don't know how to solve it ..i have tried startx command it doesn't help me....but my friend's s/m configuration is different from mine.....how to solve it without reinstallation ??

ya it shows the error GLIBC2.0 not found

---

### Post by navaneethan on 2009-02-25
> **navaneethan said:**
> Friends my self Navaneethan i have installed ubuntu hardy and also my friend also have installed it as well as he updated many suites   for hardy over internet.i also want to install those packages...so i searched how to install those packages without inet..i had a method that is  i copied all packages from ubuntu cache in my friend's hardy ...then copied those packages into my desktop and i typed the command "sudo dpkg -i *.deb" all packages have updated after i restart my computer then it doesn't enter into graphical login(doesn't ask user name and passwd in gui mode)..it localhost login in blank screen ...then i don't know how to solve it ..i have tried startx command it doesn't help me....but my friend's s/m configuration is different from mine.....how to solve it without reinstallation ??

ya it shows the error GLIBC2.0 not found

---

### Post by Flyingjester on 2009-02-25
reinstall would be my suggestion

---

### Post by ugm6hr on 2009-02-25
A few pointers:

1. Installing random .deb files is generally not a good idea.

2. You should still be able to log in at the terminal.

3. You can find out what packages are required to fix with:
```
sudo apt-get install -f
```

4. Undoing the damage will require you to identify which packages were *not* installed prior to your "update" and un-installing them.

5. It is likely that reinstalling will actually be faster.

6. If you want to install *appropriate* updates:
Copy the .deb files from your friend's /var/cache/apt/archives (except lock) to your equivalent directory (using "sudo" privileges), then run **sudo apt-get update**

---

### Post by navaneethan on 2009-05-09
Thanks  If any solution available to remove GLIBC problem

---

