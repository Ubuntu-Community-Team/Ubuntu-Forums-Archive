---
title: "file access and delating issues"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by OddJoe69 on 2010-10-11
Hi Everyone,

Ok so I installed gmount-iso and mounted a iso image, installed a game, unmounted everything....but there are still all the mounted files on my desktop. The files are locked and it will not let me do anything with them. I am trying to delate the files and clear up the space on my hard drive.

It also says I am not the root user. I have been trying to do things with the sudo command, but nothing is working. I tryed looking in my root folder, and it said I dident have premishen and wouldent let me view anything. How can I fix this? I am useing Ubuntu 10.10. 

Thanks in advance for any help you give.

---

### Post by diablo75 on 2010-10-11
Well, I'm not sure why those files aren't accessable (perhaps they ISO was mounted with sudo?), but you could run an instance of the Nautilus file browser as root (temporarily) and delete the files that way.

Just open a terminal and type:

```
gksu nautilus
```

Press Enter, type your password and press enter again.  This new window will pop up.  Go to the root directory of the file system and look for the Home folder, and then your user account name within it (that's your home folder).  From here you should be able to find the files in question and delete them.

---

### Post by OddJoe69 on 2010-10-12
oddjoe@OddBall:~$ gksu nautilus
Initializing nautilus-gdu extension

(nautilus:13400): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '13400'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:13400): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

---

