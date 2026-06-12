---
title: "CLI running .sh file"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by squee on 2009-05-01
Ok trying to run JSMS.sh

It exists in   /home/USER/JSMS/JSMS.sh

I want to create a launcher for it on the desktop, but I cant get it to work. What command should I be using there?


If that isn't possible, I've been trying to run the program from the command line but it is strange. If I type: cd JSMS   then  sh JSMS.sh it works, but if I type  cd JSMS | sh JSMS.sh   it doesnt work.

Any ideas? thanks guys.

---

### Post by taurus on 2009-05-01
Does it run if you run this?

```
sh ~/JSMS/JSMS.sh
```
Otherwise, make sure JSMS.sh has an executable permissions.

```
cd ~/JSMS
chmod 755 JSMS.sh
cd
~/JSMS/JSMS.sh
```

---

### Post by squee on 2009-05-01
I've made it executable but still wont run with those commands.

Edit: It does work now if I do sh ~/JSMS/JSMS.sh in the terminal, but not as a launcher.

---

### Post by taurus on 2009-05-01
Which command, ~/JSMS/JSMS.sh?

---

### Post by taurus on 2009-05-01
How did you create a launcher for it?

---

### Post by Bios Element on 2009-05-01
Do you have this at the top of the file?
```
#!/bin/bash
```

---

### Post by squee on 2009-05-01
"
#!/bin/sh
"
is at the top of the file. Should I replace it?


created launcher by rightclicking on desktop...

---

### Post by taurus on 2009-05-01
What did you put in for the **Comm_a_nd:** field?

---

### Post by squee on 2009-05-01
Command field: sh ~/JSMS/JSMS.sh

---

### Post by taurus on 2009-05-01
Remove the **sh** in front, just ~/JSMS/JSMS.sh.

---

### Post by Wobblybob on 2009-05-01
> **squee said:**
> Command field: sh ~/JSMS/JSMS.sh

try just ~/JSMS/JSMS.sh in the Command field

---

### Post by squee on 2009-05-01
> try just ~/JSMS/JSMS.sh in the Command field 

Cant believe this. Doesnt work: "Details: Failed to execute child process "~/JSMS/JSMS.sh" (No such file or directory)"

but it clearly exists. I'm looking at it! :lolflag:

Path is definately  Home/USER/JSMS/JSMS.sh

---

### Post by brunogirin on 2009-05-01
Try to give it the fully qualified path instead: /home/USER/JSMS/JSMS.sh

---

### Post by taurus on 2009-05-01
Try the absolute path then.

```
/home/USER/JSMS/JSMS.sh
```
Also, probably a good idea to change 

```
#!/bin/sh
```
to 
```
#!/bin/bash
```

---

### Post by DGortze380 on 2009-05-01
> **squee said:**
>  If I type: cd JSMS   then  sh JSMS.sh it works, but if I type  cd JSMS | sh JSMS.sh   it doesnt work.

Any ideas? thanks guys.

because you don't want a pipe, you want a logical and.

cd JSMS && ./JSMS.sh

---

### Post by squee on 2009-05-01
> **taurus said:**
> Try the absolute path then.

```
/home/USER/JSMS/JSMS.sh
```
Also, probably a good idea to change 

```
#!/bin/sh
```
to 
```
#!/bin/bash
```


Done. Still not working. I've had enough for tonight need sleep. Thanks for all the help guys. Atleast I know what I should be doing now.

---

