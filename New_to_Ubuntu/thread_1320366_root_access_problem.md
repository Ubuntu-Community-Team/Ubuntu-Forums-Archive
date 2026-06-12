---
title: "root access problem"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by dhanabalan_svks on 2009-11-09
hi i am not able to access root via terminal.if i use sudo command i get below error..
 sudo: /etc/sudoers is mode 0777, should be 0440

Synaptic package not able to access.But i am not getting any error.
 
 Please help me

Regards,
[EMAIL="dhanabalan.c@npediatech.com"]dhanabalan.c@npediatech.com[/EMAIL]

---

### Post by nothingspecial on 2009-11-09
```
sudo chmod 0440 /etc/sudoers
```

You didn`t make everything 0777 did you? That could get messy.

---

### Post by nothingspecial on 2009-11-09
Thinking about it a bit, if you can`t sudo that`s not going to work.

Boot into recovery mode and issue that command without sudo.

---

### Post by dhanabalan_svks on 2009-11-09
I am using below command :
 
**sudo chmod 0440 /etc/sudoers** .But i get below error[B]

sudo chmod 0440 /etc/sudoers[/B].

I am not able to login as a root.I use below command 
sudo -su

Help ....

---

### Post by nothingspecial on 2009-11-09
Reboot and when the grub dialogue appears hit escape.

From the menu, choose recovery mode then boot into a root maintanence shell.

```
chmod 0440 /etc/sudoers
```

Then reboot.

Like I asked, you`ve not made your whole system 0777 have you?

---

### Post by dhanabalan_svks on 2009-11-09
No
But i have folder named as test

I set a permission like below

 sudo chmod 0777 test/*/*/*/*/*

---

### Post by Unitux on 2009-11-09
Not from your home directory as it seems :(

---

### Post by nothingspecial on 2009-11-09
I`ve got a horrible feeling you`ve hosed your system.

Did you try the command from the recovery console?

---

