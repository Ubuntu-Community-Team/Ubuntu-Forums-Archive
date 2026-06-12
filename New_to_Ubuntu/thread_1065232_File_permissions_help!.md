---
title: "File permissions help!"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by pyktas on 2009-02-09
Hello everyone, i'm absolute beginer.. The problem is with permission.. when i'm trying to instal any driver terminal making errors and writing that permission is denied.. i just want to know how to open permission? 


              Sorry for my bad englsh.

---

### Post by joey-elijah on 2009-02-09
Type the word 'SUDO' before whatever your terminal command is.

 SUDO is what gives you permission (providing you have the correct password)

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

---

### Post by pyktas on 2009-02-09
thank for the help, i will try.

---

### Post by Gannon8 on 2009-02-09
> **joey-elijah said:**
> Type the word 'SUDO' before whatever your terminal command is.

 SUDO is what gives you permission (providing you have the correct password)

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

By the way, it's "sudo", not "SUDO". Linux, like humans, are cAsE-sEnSiTiVe.

---

### Post by pyktas on 2009-02-09
Gannon8 it's ok everything are working now :) ty for the help..

---

### Post by shad0w_walker on 2009-02-09
What drivers are you trying to install? I haven't had to install a driver from the command line for a good couple of years now.

---

### Post by pyktas on 2009-02-09
i'm trying to make my belkin wireless adapter to work and my s3 video graphic ****.. first i installed s3 graphics than rt2570 usb drivers **** and ndiswrapper- 1.54 .

---

### Post by unplugged23 on 2009-02-09
ubuntu runs a little differently than most linux distros in the way that even when your logged in as the first person registered on the machine, its not always running in root mode. meaning you wont ALWAYS have permission to change all files and settings without being prompted for your root password (which is your user pass provided your the first user on the machine) so when your in terminal and you tell it to do an administrative task, the machine wont allow it unless its been supplied with your root password. when you type "sudo" before your command it will know that your the admin and prompt you for your pass, if you enter it correctly it will carry out the command.

---

