---
title: "Permission Denied on flash installation"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by StanW22 on 2011-01-21
I just successfully created and booted Ubuntu on a flash drive.  I am now trying to use "app-get install" command from the root directory (i think).  I'm getting a message access denied and don't know why i'm getting this error.

I've never used Ubuntu before and am just learning linux too.

I would appreciate comments/assistance as soon as possible.

Thanks,
Stan

---

### Post by Verbeck on 2011-01-21
apt-get should be used with sudo
eg; *sudo* apt-get install foobar

---

### Post by ubudog on 2011-01-21
> **Verbeck said:**
> apt-get should be used with sudo
eg; *sudo* apt-get install foobar

That should do it.  Also, note that you won't see your password being entered (not even asterisks or anything).  But it is still there.  :p

---

### Post by StanW22 on 2011-01-21
I successfully installed and booted Ubuntu (for the first time) on an HP laptop running Vista.  Using  the Terminal interface i type in: $ apt-get install chntpw  

I got an error message access denied.  I believe I was using the root directory, but not 100% sure.

I am hoping there's a fairly straight-forward explanation for this problem.  I'm new to Linux and Ubuntu.  I've read several key chapters of the Linux 2011 Edition Bible by Christopher Negus in addition to reading about linux distros on the net and I am just now trying to do some real work using Ubuntu to recover the admin password on my HP laptop.

Please help.

Thanks,
Stan

---

### Post by Smart Viking on 2011-01-21
You muse use sudo in front to get root privileges, like this:
```
sudo apt-get install chntpw  
```

---

### Post by StanW22 on 2011-01-21
hey there smart viking.. this is my first thread on Ubuntu forums.  I don't understand why the status is showing "solved" already.   

I tried sudo etc. as you suggested and got another error.  Unable to locate package.  I just installed abuntu to this 1GB flash drive.  And now I need to get the chntpw to reset the admin password in vista.

I suspect the the command is looking for chntpw on the flash drive first.  Can i use the abuntu software center to finds this app or a comparable one?

I'm following instructions from this link to this work:  [http://linuxtree.blogspot.com/2010/01/how-to-recover-hack-reset-windows.html](http://linuxtree.blogspot.com/2010/01/how-to-recover-hack-reset-windows.html)


Can I reset this thread to unsolved or do I need to open a new thread?

---

