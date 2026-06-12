---
title: "What's the difference between Root Terminal and Terminal?"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by ni ni on 2009-03-16
Hi All,

What's the difference between Root Terminal and Terminal?

If I'm asked to type something into Terminal which one should I go for?


Thank you all! x x x x

---

### Post by mhgsys on 2009-03-16
in a terminal you become root so you can edit files as a superuser
as a user you cannot change files like /etc/X11/xorg.conf for example.

---

### Post by perlluver on 2009-03-16
> **ni ni said:**
> Hi All,

What's the difference between Root Terminal and Terminal?

If I'm asked to type something into Terminal which one should I go for?


Thank you all! x x x x

Normally if someone gives you a command on here, you would run it from the normal terminal.  The root terminal gives you root access, for as long as it is open.  Normally on here, we would give you a sudo command, which you would run under a normal terminal, and root ends when the sudo command ends.  Either way the choice is up to you, but I would recommend the normal terminal.

---

### Post by ni ni on 2009-03-16
:KS:KS:KS:KS:KS:KS

So if i type sudo + my command, it is the same as being in the root terminal, but I finish being a root user right after the command has been executed?

---

### Post by Therion on 2009-03-16
> **ni ni said:**
> So if i type sudo + my command, it is the same as being in the root terminal, but I finish being a root user right after the command has been executed?
For all intents and purposes, yes.  Actually, using "sudo" once maintains your root status for 5 minutes or some such.

---

### Post by Linux000 on 2009-03-16
Yes, sudo puts you as root for the duration of the command, this is a safer way to go, as if you stay root and a virus somehow infects the account, it could infect the whole computer, if you are non-root, it can only affect your folder, this is the marvel of linux security

---

### Post by mhgsys on 2009-03-16
> **ni ni said:**
> :KS:KS:KS:KS:KS:KS

So if i type sudo + my command, it is the same as being in the root terminal, but I finish being a root user right after the command has been executed?

correct.

---

### Post by ni ni on 2009-03-16
Thank you everyone!

.... now how do i mark this as solved...

---

### Post by mhgsys on 2009-03-16
lol, 

I'm not sure. 

I guess to add.

[SOLVED]

---

### Post by bubwitmaingay on 2009-03-16
> **ni ni said:**
> :KS:KS:KS:KS:KS:KS

So if i type sudo + my command, it is the same as being in the root terminal, but I finish being a root user right after the command has been executed?

Their is no difference with the "Normal" Terminal and Root Terminal. Both can be launched in the same terminal. The catch is that you will change from user privilege to super-user privilege within the same terminal, just by typing this code:
```
su
```
it will ask for your password (the one you use when you logged-in). 
The difference between user and super-user (root) is the ability to change setting and preferences on files and folders. Some files and folders are "locked" or protected in the root, thus only the root can unlock it. Most applications that can only be installed through line or terminal, needs super-user privilege, thus only a root can install it in your machine (system).
The main disadvantage of Root user though is the ability to mess around with your system. The root can assessed all the files and modify them - a mistake in deleting some system file will really ruin your OS.

Hope that helps. 8)

---

### Post by bubwitmaingay on 2009-03-16
Oh I forgot. Before you can be a super-user at the terminal, you should manage your users and groups first.

1. Go to *Systems>Administration>Users and Groups*
2. Click the "Unlock" button at the "User Settings" window and an authentication window will appear and asks for your password (as user), then click the "Authenticate" button.
3. You will observe that the root user can now be modified and visible, choose that and the "Properties" and "Delete" buttons will now be visible. Click the "Properties" button.
4. If you want to change your password for the root user, you can do so with the new window "Account 'root' Properties" (but i recommend you leave it as blank). Click the "User Privileges" tab and tick every box. If you are done, click "Ok".
5. It will return to the "User Settings" window, click the "Close" button.
6. You are done and your root (super-user) is activated.

Again, I hope that helps. 8)

---

### Post by ni ni on 2009-03-16
Thank you!

---

### Post by anewguy on 2009-03-16
To mark as solved for now:

go back to your original post

select edit then advanced - in advanced you are allowed to change the title.  Just as [SOLVED] to the front of the title and save.

Dave :)

---

### Post by ni ni on 2009-03-16
Thanks dave,

i already tried that!

then i found out it is a bandwith thing or something - they have taken it away deliberately!

---

### Post by anewguy on 2009-03-16
Yes, they took away the normal way to mark a thread as solved, however you can still edit the title like I said to let others know you have your solution.

Dave :)

---

