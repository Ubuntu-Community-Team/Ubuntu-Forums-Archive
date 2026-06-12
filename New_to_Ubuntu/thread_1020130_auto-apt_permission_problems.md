---
title: "auto-apt permission problems"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Roflmewafflez on 2008-12-23
When I tried to compile a program from a .tar.bz2 folder I followed the instructions on [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) but when I got to the auto apt running for the directory this happens

wafflez@wafflez-laptop:~$ auto-apt run /usr/local/src/cinelerra-4-ubuntu-i686
Entering auto-apt mode: /usr/local/src/cinelerra-4-ubuntu-i686
Exit the command to leave auto-apt mode.
exec: 530: /usr/local/src/cinelerra-4-ubuntu-i686: Permission denied

If I didn't have administrative privileges this would make sense but I set the permissions so my account had every available privilege

How can I get past this?

---

### Post by northern lights on 2008-12-23
Your account is most likely in the admin group. As such you have the rights to assume temporary superuser privileges.

However can only alter files in your /home folder by nature. auto-apt needs to be run as root:```
sudo auto-apt ...
```

---

### Post by mrbiggbrain on 2008-12-23
> **northern lights said:**
> Your account is most likely in the admin group. As such you have the rights to assume temporary superuser privileges.

However can only alter files in your /home folder by nature. auto-apt needs to be run as root:```
sudo auto-apt ...
```

anytime you do anything that affects anyone, even remotely other then yourself, or affects anyone who may ever exist, past present, or future you have to be root, you can always use sudo if your privileged anough.

---

### Post by Roflmewafflez on 2008-12-23
I tried adding on the sudo to the code, and the same problem happened

---

