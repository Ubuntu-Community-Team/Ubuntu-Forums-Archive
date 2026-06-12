---
title: "chrootkit scripting help"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-05-01
i have added the following script to the startup apps file however it runs silently how do i modify the script so it will run in the terminal when it starts/tks

#!/bin/bash
sudo  chkrootkit 
sleep 3

---

### Post by rburkartjo on 2009-05-01
just to clarify i want to see the output run when it starts

---

### Post by decoherence on 2009-05-01
try putting

```
xterm -e nameOfYourScript.sh
```

in your list of startup programs. Or if you prefer to modify the script itself,

```

#!/bin/bash
xterm -e sudo chkrootkit
sleep 3

```

In either case, the magic you want is 'xterm -e' (run xterm and execute the following commands)

---

### Post by rburkartjo on 2009-05-01
deco, what did i do wrong
left script the same
add the following to startup
run chkrootkit
xterm -e run chkrootkit.sh

and get the following error message when i login

xterm: Can't execvp run:No such file or directory
ray@ray-desktop:~$

---

### Post by rburkartjo on 2009-05-01
note the script is on my desktop

---

### Post by nandemonai on 2009-05-01
> **rburkartjo said:**
> note the script is on my desktop

Use the full path /home/username/Desktop/scriptname

---

