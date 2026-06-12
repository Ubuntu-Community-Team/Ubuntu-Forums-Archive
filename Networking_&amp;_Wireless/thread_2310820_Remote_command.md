---
title: "Remote command"
date: 2016-01-22
forum: Networking &amp; Wireless
---

### Post by zkab on 2016-01-22
I have a remote server 'r_server' and I want to execute a script 'sum.sh' remotely from my workstation.
The script 'sum.sh' on the remote server is in a directory 'my_scripts' (in home dir) and looks like this:
-----------
#!/bin/sh

script1.sh
script2.sh
script3.sh
-----------
The script1-3.sh are also located in the same remote dir 'my_scripts' but when I execute 

   ssh user@r_server "my_scripts/sum.sh" 

it complains that script1-3.sh are not found.
When I ssh to 'r_server' explicitly and execute 'sum.sh' it works just fine ...

---

### Post by Henrik_LIndstrm on 2016-01-22
Maybe if you put the full path to the other scripts in sum.sh like ~/my_scripts/script1.sh etc?

---

### Post by zkab on 2016-01-22
Have tried that also - same sad result ...

---

### Post by ajgreeny on 2016-01-22
Are the scripts marked as executable?

If they are go one step further with the remote command using the full pathway of 
```
ssh user@r_server/home/username/my_scripts/sum.sh
```
You do not need the quotation marks as there are no spaces in the pathway to escape, thiough adding them should not stop it working as far as I'm aware.

---

### Post by zkab on 2016-01-22
Yes they are marked as executable.
Changing to ssh [email]user@r_server/home/username/my_scripts/sum.sh[/email] still gave me the error ...

---

### Post by ajgreeny on 2016-01-22
> **zkab said:**
> Yes they are marked as executable.
Changing to ssh [email]user@r_server/home/username/my_scripts/sum.sh[/email] still gave me the error ...

Can I assume you did not actually type the word "username" but used the actual username?

---

### Post by zkab on 2016-01-23
When I added the remote servers PATH to the command it solved the problem ...

ssh user@r_server "PATH=$PATH:the path for remote server; my_scripts/sum.sh"

---

