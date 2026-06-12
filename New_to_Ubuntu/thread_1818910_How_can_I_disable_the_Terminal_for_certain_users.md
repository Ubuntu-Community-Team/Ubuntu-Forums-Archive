---
title: "How can I disable the Terminal for certain users?"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by jakecersi on 2011-08-05
I want only certain users to be able to use the Terminal if possible.

---

### Post by melrokz on 2011-08-05
Terminal is the command line interface of Ubuntu, similar to 'Command prompt' in Windows, but it is much more important in Linux.

Disabling the Terminal? You are asking to disable the command interpreter which would make Ubuntu or any other operating system useless!

You may as well not create a user account for those users who need not run any commands on Ubuntu ;)

***If you intend to restrict users as to which command they can run as administrator or root, you need to edit the sudoers file.

---

### Post by Basher101 on 2011-08-05
Is there a thread on how to restrict users? I want to create an user account for my little brother - i used the chmod command alot so he cant mess with the files, as for other stuff i dont know how to restrict them. Could you give more info on how to restrict users?

---

### Post by jakecersi on 2011-08-05
Most computer users do not have any interest in using a Terminal. They use the computer mainly for browsing the Internet and word processing. There has to be a way to simply disable the the gnome-terminal for non-administrator users.

---

### Post by jakecersi on 2011-08-05
Basher101, that's exactly what I was thinking of. This seems like a really simple thing to do. Anybody have anymore suggestions?

---

### Post by Basher101 on 2011-08-05
Glad i could help^^ there are also very detailed threads on how to use the chmod command, just use the search

---

### Post by relay_man on 2011-08-06
I'm not 100% sure how to go about defeating a determined and knowledgeable user, but if you are just trying to block a casual user who might accidently damage the system from the command line, I suggest the following:

Create an account for this person @ System > Administration > Users & Groups

Set the user type for little brother to "desktop account"

This does not keep little brother from opening a terminal session, but he cannot install or remove software packages, cannot invoke any command from terminal that requires the use of "sudo", and cannot make changes to the system properties from the command line or GUI.
(Unless a past experience leads you to believe otherwise, I ask that you consider not taking away the terminal completely.  It is generally a very good thing for ALL Unix/Linux users to have knowledge of the command line interface. Even if that knowledge is gained by just messing around...)

If you feel you must take the terminal away, then:

While in little brothers account, if he isn't too snoopy you can go to System > Preferences > Main Menu
click on Accessories and un-check the box next to terminal so that it cannot even be seen from the menu.

There are other options available when you set up this account, but is this enough?

---

### Post by SavageWolf on 2011-08-06
Why do you want to do this anyway?

---

### Post by bodhi.zazen on 2011-08-06
> **jakecersi said:**
> I want only certain users to be able to use the Terminal if possible.

Find any terminals you have installed (gnome-terminal, xterm, etc)

```
sudo addgroup terminal
sudo chrgp terminal /bin/your_terminal
sudo o-x /bin/your_terminal
```

xterm is in /usr/bin/xterm

Now add any users you want to access the terminal to the terminal group. 

> **SavageWolf said:**
> Why do you want to do this anyway?

This is a better question, why bother ? Unless they have access to sudo they can not damage the system.

---

### Post by itcotbtoemik on 2011-08-07
That breaks the utmp feature for xterm, unless the Ubuntu's
updated to use utempter.

---

