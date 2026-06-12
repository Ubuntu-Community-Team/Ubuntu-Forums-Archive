---
title: "Root/su Password and Sudo?"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by jrenaldy on 2010-11-18
Ok, please bear with me.  I recently installed Ubuntu on my laptop and I've found that I can pretty much do everything that I was doing when I had Windows.  However, I've run into a bit of a snag.  I've tried to install a Cisco VPN from where I work in order to access my company's sever.  Everything starts off well until I receive a message asking me for my root/su password.  I've tried to research the matter but I think I'm making things worse; at least in my head.  I came accross something called "sudo" and apparently it will bypass the need for a root/su password.  Any help would be greatly appreciated!

---

### Post by matt_symes on 2010-11-18
Hi

In Ubuntu there is no root password by default and the root account is locked. 

The way to get root privileges in Ubuntu is to prepend any command that requires root privileges with the word sudo. It will then ask for a password. This will be your password and if entered correctly the command will be executed.

i.e. In a terminal

matthew@matthew-laptop:~$ sudo apt-get update
[sudo] password for matthew: 

If the correct password (my password) is entered then the command (apt-get update) will be executed.

In a graphical environment you would use

gksudo <command>

and this will run a graphical program with root privileges. This can be run from the terminal or by pressing Alt+F2 and entering the command.

The privileges for a user are located in the sudoers file.

sudo cat /etc/sudoers

This is all part of Ubuntu security policy and helps to make Ubuntu safe. I hope this clarifies things

  > Everything starts off well until I receive a message asking me for my root/su password. At what point does this happen?
What are you doing?
This sentence needs clarification.

Kind regards

---

### Post by azertyh on 2010-11-18
hello,
to be clear [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

