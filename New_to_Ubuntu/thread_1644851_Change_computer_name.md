---
title: "Change computer name"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by cf0531 on 2010-12-13
Is there a way to change the computer name after installation i just recently reinstalled ubuntu after using kubuntu for a bit and it defaulted to using this long obnoxious name for my computer, can I change this and how.

thanks

---

### Post by tgm4883 on 2010-12-13
> **cf0531 said:**
> Is there a way to change the computer name after installation i just recently reinstalled ubuntu after using kubuntu for a bit and it defaulted to using this long obnoxious name for my computer, can I change this and how.

thanks

```
hostname --help
```

---

### Post by StephenDavison on 2010-12-13
Open a terminal.
Type the following command:   man hostname
Read about it.

```
sudo hostname <new host name>
```edited to add:
Oops, looks like tgm4883 beat me to it while I was typing.
cheers,

---

### Post by Bluebuddy on 2010-12-13
System -> Administration -> Users and Groups -> Change...

---

### Post by Badabling on 2010-12-13
Welcome !

You can change the file /etc/hostname and update to your new hostname,  you can then run /etc/init.d/hostname.sh to activate  the change.
 - Update your /etc/hosts file to the hostname

Lol didn't knew there where THAT much ways to change it xD

---

