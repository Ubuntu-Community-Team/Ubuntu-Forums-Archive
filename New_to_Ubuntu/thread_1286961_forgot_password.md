---
title: "forgot password"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by aparolin on 2009-10-09
problem,
tried to download distro for ubuntu 9.04 and install the package.  when asked for password; i forgot it...

is there a way to retrieve password or will i have to change it?  

if not; next question, (how to change it)

---

### Post by sisco311 on 2009-10-09
Reset your password from the *Recovery Mode*:

[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by rburkartjo on 2009-10-09
sisco tks for that link also

---

### Post by aparolin on 2009-10-09
thanx for replying;

followed instructions and when i arrived at root recovery menu;
i went down to:
"netroot--drop to root shell prompt with networking"
hit enter
it asks:
"give root password for maintenance or type control-d to continue"
typing control-d to continue brings me back to the root recovery menu

stuck again

---

### Post by aparolin on 2009-10-09
should i be disconnected from the net???

---

### Post by rburkartjo on 2009-10-09
apa try this
If you forgot you password for your ubuntu system you can recover using the following steps 
Turn your computer on.
Press ESC at the grub prompt.
Press e for edit.
Highlight the line that begins kernel recovery………, press e
Go to the very end of the line, add rw init=/bin/bash
press enter, then press b to boot your system.
Your system will boot up to a passwordless root shell.
Type in passwd username
Set your password.
Type in reboot

---

### Post by rburkartjo on 2009-10-09
this worked for me cause i had to use it when i first started using ubuntu a couple of years ago

---

### Post by sisco311 on 2009-10-09
> **aparolin said:**
> should i be disconnected from the net???

This is why is no recommended to set up a root password in ubuntu. By default, if the root account password is locked you can boot in recovery mode without being asked for a password.

Anyway, reboot

highlight the recovery mode line,

hit e for edit, highlight the line that begins kernel, 

hit e for edit, delete the *ro single (splash quiet)* options from the end of the line

type *rw init=/bin/bash*, hit Enter

and hit b to boot.


The computer should boot in a root shell. From there you can reset your password:

```
password *username*
```

Press Ctrl+Alt+Delete to reboot.

EDIT: too late. :)

---

### Post by sisco311 on 2009-10-09
> **rburkartjo said:**
> this worked for me cause i had to use it when i first started using ubuntu a couple of years ago

It still works with a little modification.

You have to delete the *ro quiet splash*(at least the splash) option from the kernel line before adding *rw init=/bin/bash*.

EDIT: 
last when i tried, the reboot command doesn't worked, that's why i suggested Ctrl+Alt+Del.

EDIT2:
OP: please read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

make sure that your main user is able to use sudo and re-disable the root account password.

---

