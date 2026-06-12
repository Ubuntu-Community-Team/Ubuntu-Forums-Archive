---
title: "SElinux or protector thingy?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by cooper77z on 2009-07-14
What's more appropriate for a server?

---

### Post by steveneddy on 2009-07-14
protector thingy?

:|

---

### Post by jerome1232 on 2009-07-14
By protector thingy do you mean apparmor?

---

### Post by binbash on 2009-07-15
selinux is a must

---

### Post by cooper77z on 2009-07-15
Yea, I meant aparmor. Thanks, I'll switch to selinux if I can remember the sudo command.

Do I just type this into the terminal and reboot to switch?


[LIST=1]
[*]Install selinux:
[LIST]
[*]> apt-get install selinux
[/LIST]
 
[*]Reboot
[/LIST]
It won't let me issue the command. It asks me if I am root. But then it won't let me answer. What do I do to install selinux instead of apparmor?

Here is the error I am getting"E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

---

### Post by 3rdalbum on 2009-07-15
> **cooper77z said:**
> Yea, I meant aparmor. Thanks, I'll switch to selinux if I can remember the sudo command.

Do I just type this into the terminal and reboot to switch?


[LIST=1]
[*]Install selinux:
[LIST]
[*]> apt-get install selinux
[/LIST]
 
[*]Reboot
[/LIST]
It won't let me issue the command. It asks me if I am root. But then it won't let me answer. What do I do to install selinux instead of apparmor?

Here is the error I am getting"E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

You need to put "sudo" in front of that command. Sudo tells the system to run that command as root; and of course only root is allowed to install software.

Installing SELinux is not as easy as just installing it - it needs to be configured. I'm concerned that configuring it is probably beyond your capabilities at this time. You will find it easier just to get some premade AppArmour profiles for the services you want to secure, and for your purposes it will be just as secure.

I *am* curious as to what server you are running...

---

### Post by bodhi.zazen on 2009-07-16
If you want to try SELinux, and you are on a server, I suggest you go with Centos.

If you want to stay with Ubutnu, go for Apparmor.

Installing selinux on Ubuntu can be difficult.

---

### Post by AndThenWhat on 2009-07-16
> **steveneddy said:**
> protector thingy?

:|

:lolflag:

---

### Post by cooper77z on 2009-07-16
3rd, "Installing SELinux is not as easy as just installing it - it needs to be configured. I'm concerned that configuring it is probably beyond your capabilities at this time."

You are really tempting me to do it anyway. But, when I modified ubuntu studio to selinux it tripled my system performance that I appreciated on gnome. Specifically, what needs to be configured?

Oh yea, I am running server 8.04.2 with the updated gnome that comes with epiphany.

---

