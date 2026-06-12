---
title: "Help Permission Deined"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by joec369 on 2009-03-04
Very new to Ubuntu and Linux.  I'm trying to copy some theme files for some pacakage called ubuntulooks to the /usr/share/theme directory.  But for some reason i can't copy files there is say permision denied.  I tired drag and drop.  And in terminal.  In terminal I went sudo -l  It ask for my password and I gave it.  It said all command available.  Still didn't work when I tried it with the mv command.

Please help!!

---

### Post by Majiq on 2009-03-04
So in order to change the /usr/share/theme directory, you need super user access. You apparently know about sudo. I would suggest one of two things:

1. Press Alt+F2 to open up the "Run Application" setup and type in command 'gksudo nautilus'. In case you don't know, gksudo is a graphical version of sudo, appropriate for commands not in the terminal. Then do your copying and such.

2. In the terminal, you should type your mv command (i.e. "mv source destination") but prepend the entire command with the sudo (i.e. "sudo mv source destination"), because sudo -l just lists available commands. Following sudo by a command says to run that command. If you wanted to drop into a root shell, (so you wouldn't have to say sudo each time) you could use sudo -s and then use the commands you saw from sudo -l.

---

### Post by joec369 on 2009-03-04
Thank you it worked !!

---

