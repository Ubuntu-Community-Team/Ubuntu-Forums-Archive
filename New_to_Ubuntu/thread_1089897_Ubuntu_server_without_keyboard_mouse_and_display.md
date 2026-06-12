---
title: "Ubuntu server without keyboard mouse and display"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by skippyb on 2009-03-07
Have managed to setup a ubuntu server and installed Nomachine both on server and windows pc, connection ok! but how do i boot the server and start all the needed applications without keyboard mouse and display?

---

### Post by thtrgremlin on 2009-03-07
well the power button should turn on the computer, and everything should startup fine. Typically one would use SSH to connect to the server machine to do any necessary management.

openssh should have been setup by default if you did a server install.

If you only have Windows with a keyboard, mouse, and monitor, I am sure there are ssh clients for windows that you can use to connect, but not sure all what they are. I have heard of PuTTY and cygwin, but have not used them.

What are you planning on using the server for, if you don't mind be asking? Just curious that you would have a setup like this but not familiar with ssh, but how do you learn if you don't try, right?

---

### Post by skippyb on 2009-03-11
> **thtrgremlin said:**
> well the power button should turn on the computer, and everything should startup fine. Typically one would use SSH to connect to the server machine to do any necessary management.

openssh should have been setup by default if you did a server install.

If you only have Windows with a keyboard, mouse, and monitor, I am sure there are ssh clients for windows that you can use to connect, but not sure all what they are. I have heard of PuTTY and cygwin, but have not used them.

What are you planning on using the server for, if you don't mind be asking? Just curious that you would have a setup like this but not familiar with ssh, but how do you learn if you don't try, right?

Hi.
Got it to work :D, first had to turn off halt on errors in bios, then i had to enable automatic login in "Login window preferences" under security. Shut down server, removing keyb,mouse and display cables, reboot server and started NX client for windows, can now remotely access server;)

I&#7743; planning to use server to store images, music and movies for sharing with the rest of the computers in our family (6)+ the printer.

---

### Post by thtrgremlin on 2009-03-12
auto login? are you running a desktop environment on the server and using remote desktop? Hmm... never heard of doing it that way, but guess that works! Gratz.

---

### Post by linuxisevolution on 2009-03-12
You will have to install ssh on the server, and then on your desktop, and then you can connect to the server with the command:


ssh -X [email]username@XXX.XXX.XXX.XXX[/email]

replace the X's with the server's ip address and username with your username on the Ubuntu server. -X means you will be able to run programs that require X, like firefox or nautilus (although I only use it for thunar).

---

