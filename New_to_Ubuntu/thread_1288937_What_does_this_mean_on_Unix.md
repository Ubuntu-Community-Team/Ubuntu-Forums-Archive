---
title: "What does this mean on Unix?"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by afroman10496 on 2009-10-12
I was playing with some other *nix's like OpenSolaris and BSD and I was trying ```
sudo apt-get update
``` on Opensolaris (I know it doesn't have apt but I was curious:)) and it said ```
Password:
joe is not in the sudoers file.  This incident will be reported.
```
What does that mean and do I get to see the naughty thing that I did if I log in as root?

---

### Post by coldReactive on 2009-10-12
You aren't a sudoer:

> You can do the following to enable sudo for the wheel group:

1) Edit /etc/sudoers, uncomment the line: %wheel ALL=(ALL) ALL
2) Create a group called wheel and add yourself, using the GUI or the following commands:

$ pfexec groupadd wheel
$ pfexec usermod -G wheel $USERNAME

3) No need to logout, open a new terminal and try sudo

---

### Post by afroman10496 on 2009-10-12
> **coldReactive said:**
> You aren't a sudoer:
cool thanks

---

### Post by BorgHunter on 2009-10-12
And you can check /var/log/auth.log to see your naughtiness:
```
borghunter@ares ~ $ su ares
Password:                  
ares@ares:/home/borghunter$ sudo ls
[sudo] password for ares:          
ares is not in the sudoers file.  This incident will be reported.
ares@ares:/home/borghunter$ exit                                 
borghunter@ares ~ $ cat /var/log/auth.log | grep sudoers
Oct 11 23:12:27 ares sudo:     ares : user NOT in sudoers ; TTY=pts/1 ; PWD=/home/borghunter ; USER=root ; COMMAND=/bin/ls
```

---

