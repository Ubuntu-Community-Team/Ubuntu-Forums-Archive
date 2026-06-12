---
title: "Synaptic Package Manager Error"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by jsdieorksw on 2009-07-25
Whenever I start up the package manager I get this message: 

Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file. 

Anyone know what I should do?

---

### Post by Soul-Sing on 2009-07-25
please empty the /tmp directory

---

### Post by shanix on 2009-07-25
Maybe you can also check under your home directory

ls -l ~/.Xauthority

-rw------- 1 ubuntu ubuntu 272 2009-07-25 10:22 .Xauthority

to see if the permission is set properly or if the file exist or not.

---

### Post by jsdieorksw on 2009-07-25
After I cleared the tmp directory I was able to enter my password in order to access the manager (i thought it worked) but it keeps telling me that the password is incorrect.  Also I can't find that file in the home directory

---

### Post by aysiu on 2009-07-25
Do you have caps lock on?

If not, you may have to reset your password:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by jsdieorksw on 2009-07-25
No, caps lock is not on.  I've reset the password and it still doesn't work

---

### Post by llamabr on 2009-07-25
What happens when you try it from cli:

```
sudo apt-get install something
```

---

### Post by jsdieorksw on 2009-07-25
Wow, I didn't even know this...I can't even open my terminal. I don't know what happened to this thing.

---

### Post by llamabr on 2009-07-25
Did you previously run apt-get upgrade while in gnome?  Try logging out of gnome, and logging back in.

---

### Post by jsdieorksw on 2009-07-25
Terminal works, I tried to install something and it worked like normal and accepted the new password so the problem must be within synaptic package manager right?

---

### Post by jsdieorksw on 2009-07-25
God I feel like an idiot. The logging out and loggin back in did it (damn, that never works!). Package Manager works now.  Thanks for the help...maybe I should try logging out and back in more often!

---

### Post by llamabr on 2009-07-25
If you run upgrade while in gnome, when it's done some programs that are running won't exist anymore, since they're replaced with a newer version.  Logging out is one easy way to close them all.  I close x, and run updates in a tty.  glad it's fixed.

---

