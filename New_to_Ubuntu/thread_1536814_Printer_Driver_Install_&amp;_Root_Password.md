---
title: "Printer Driver Install &amp; Root Password"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by tf4545 on 2010-07-22
I have a Lexmark printer that I have downloaded the driver for.  When running the driver install, the GUI walk thru to a point which it is asking for the root password.  I have tried using my user password to no avail and then changed my user profile to admin and still had no luck.  When trying to run the installer in terminal it launches the Lexmark GUI....

What is the root password?

Thanks for all the help in advance!

---

### Post by SlidingHorn on 2010-07-22
Just leave it blank and hit enter.  Should work unless you specifically set a root pw yourself

---

### Post by tf4545 on 2010-07-22
I tried just leaving the field blank and he installer defaults back to asking if I want to abort the install as root access is required.  I just installed 10.04 on this machine earlier today and do not recall setting a root password....

Thanks!

---

### Post by lisati on 2010-07-22
By default, Ubuntu doesn't have a "root" password as such. It's more common to use the "sudo" command and then type in your current user's password. Note: your password won't show as you type it, this is a normal securtiy precaution.

Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by moorer21 on 2011-02-15
I'm having the same problem.  I understand how to use sudo in the terminal, but this is a driver installer that uses a GUI, and there is a GUI popup window that is asking for the root password, with a single password field.  Entering sudo into the field won't work.

I read the link you sent, including the part about gksudo, but again gksudo is a terminal command.

Thoughts?

---

### Post by sisco311 on 2011-02-15
> **moorer21 said:**
> I'm having the same problem.  I understand how to use sudo in the terminal, but this is a driver installer that uses a GUI, and there is a GUI popup window that is asking for the root password, with a single password field.  Entering sudo into the field won't work.

I read the link you sent, including the part about gksudo, but again gksudo is a terminal command.

Thoughts?

If you run the installer as root, then it won't prompt you for the root password:
```
gksudo path/to/file
```

---

### Post by moorer21 on 2011-02-15
Figured it out, it must be run from the command line.  Open the file with

Go to the directory the installer is in and use

sudo ./....

---

