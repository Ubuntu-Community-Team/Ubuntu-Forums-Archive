---
title: "permissions and rights"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by MVF on 2009-06-04
Although I am the administrator, as far as I can tell, when I use the command line for essential actions I am told that I do not have permission, e.g.
/boot/grub/menu.list (to change default boot OS).

Also if I try to reach /root, I am denied entry. I understsand that root rights are necessary for installing software. 

Mike

---

### Post by Celauran on 2009-06-04
You log in as a normal user with administrative privileges; it's not the same thing. Commands your normal user does not have sufficient privileges to perform need to be prefixed with 'sudo'

Example:

```
sudo vim /boot/grub/menu.lst
```

---

### Post by steeleyuk on 2009-06-04
After you install Ubuntu, you are a normal user which has permission to elevate to a higher level (using sudo). There is no root account accessible by default, to prevent people from using root all the time and potentially damaging their systems.

So, in the terminal, to edit menu.list you'd want the command:

sudo nano /boot/grub/menu.list

You might also want to run the command *man sudo* which will give you more insight into how it works.

---

### Post by yaroto98 on 2009-06-04
If you're more familiar with being a Windows Administrator, just think of it as having to "confirm" Administrator actions, like in Vista. How you confirm certain -potentially dangerous- actions is by running them as the user "root" with the command sudo (super user do). Then entering the password to confirm the action.

---

### Post by mcduck on 2009-06-04
> **MVF said:**
> Although I am the administrator, as far as I can tell, when I use the command line for essential actions I am told that I do not have permission, e.g.
/boot/grub/menu.list (to change default boot OS).

Also if I try to reach /root, I am denied entry. I understsand that root rights are necessary for installing software. 

Mike

In Ubuntu even administrator's don't run with full permissions all the time, being member of the admin group only means that you can temporarily gain administrative privileges through the use of "sudo".

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

One of the most important concepts of security in Linux/Unix systems is "using minimum force required", as in always using minimum permissions needed to complete the task.

---

