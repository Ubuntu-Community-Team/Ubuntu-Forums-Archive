---
title: "Permissions and Passwords for sudo and su"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by QuanticSakura on 2010-09-23
Hello
I installed Ubuntu 10.04 about a week ago from Wubi (I have dual-boot with Win7), first-time user with no programing skills. I don't remember being asked for any special password for root acess, just the one for my user, that supposedly has admnistrator acess, but while I can use the "sudo" command, it does not work for "su". It gave me hell today when a teacher tried to install a program that runs from the console, as apparently I don't have acess to the root  we had to create a new "/opt" folder inside my user, and some programs don'r run because the libraries are not moved properly. How can I have total acess to my machine? Do I need to reinstall Ubuntu?

---

### Post by mikewhatever on 2010-09-23
Well, sudo is pretty much equivalent to root/admin access, and if you need persistent root shell, use sudo -i.

---

### Post by mcduck on 2010-09-23
sudo works, since it requires your user password, not the target user's password.

su on the other hand needs target user's password, and since there's not one in the default Ubutnu setup you can't use "su".

If you need to open a root session in the CLI, just use "sudo -i". Although just adding "sudo" in fron of any command that requires root permissions would give prety much the same result, and is the recommended way.

You might want to read this one: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by QLee on 2010-09-23
Welcome!
[QUOTE=QuanticSakura]...
 It gave me hell today when a teacher tried to install a program that runs from the console, as apparently I don't have acess to the root  we had to create a new "/opt" folder inside my user, and some programs don'r run because the libraries are not moved properly.
...[/QUOTE]

If your goal is to learn GNU/Linux and you don't have the option of a different teacher, I suggest you will have an easier time learning if you install a distribution that the teacher is familiar with or you might face many more problems with course work due to differences in distros. It's obvious that teacher isn't familiar with Ubuntu. Maybe dual boot with Ubuntu and then learn to apply your new knowledge to Ubuntu, your education can only benefit from the effort.
Good luck!

---

