---
title: "Help with writing two simple scripts"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by humphreybc on 2009-12-31
I'd like to write a script to run my Wake On Lan command so I don't have to copy and paste it into a terminal.

How do I write this in a .sh file? What code does sh use?

And, if possible, I'd like to write one that would openssh login to the server, enter my password, and then issue a shutdown command and enter my password again.

Somehow I think the second one might be fairly hard, due to the fact it requires a password twice...

---

### Post by adelphos on 2009-12-31
So you want to write a bash script? It's basically just a list of commands, like what you would type into the terminal, so neither of those tasks should be too hard. You might want to read over a tutorial like this one:

[http://www.hypexr.org/bash_tutorial.php#whatis](http://www.hypexr.org/bash_tutorial.php#whatis)

---

### Post by Buuntu on 2009-12-31
An alternative to actually writing the script would be to just set an alias in ~/.bashrc.  Read this if you don't know how, it's pretty simple: [http://brockangelo.com/2008/10/13/create-aliases-in-ubuntu/](http://brockangelo.com/2008/10/13/create-aliases-in-ubuntu/)

---

