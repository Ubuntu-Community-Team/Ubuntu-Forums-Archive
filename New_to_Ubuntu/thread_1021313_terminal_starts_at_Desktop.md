---
title: "terminal starts at Desktop"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Dadsgé on 2008-12-25
when i open a terminal it starts at hannes@hannes-laptop:~/Desktop$ 
why doesn't he start like usual at home?
and how can i set it back to home?

---

### Post by ja660k on 2008-12-25
what terminal are you using, usually you can add an arguement to specify where you want it to start

---

### Post by Dadsgé on 2008-12-25
> **ja660k said:**
> what terminal are you using, usually you can add an arguement to specify where you want it to start

um, the terminal from the applications menu

---

### Post by Dadsgé on 2008-12-25
i found it :)
in terminal, you have a menu bar, there you go to 'terminal' and then 'reset and clear'
thanx anyway

and a merry Xmas to all of you ;)

---

### Post by ja660k on 2008-12-25
okay, this will be a tempoary solution BUT drag it to the desktop to create an alias

the open gedit, navigate to desktop and find gnome-terminal.desktop or whatever the alias is called, ctrl+f and type Exec 

find the line where it is. it should be somehting like Exec=gnome-terminal

the 2nd line after comments, anyway you want to add --working-directory=/home/YOUR_USER_NAME/

so itl look like this

Exec=gnome-terminal --working-directory=/home/YOUR_USER_NAME

---

### Post by Dadsgé on 2008-12-25
do you mean i should create a shortcut to the terminal on my desktop?
and will it keep on working if i delete that shortcut?

---

