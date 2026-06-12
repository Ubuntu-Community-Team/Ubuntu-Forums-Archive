---
title: "open terminal in different dir and run script"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-05-16
#!/bin/bash
gnome-terminal --working-directory=/home/user

the above will open a new terminal in any directory i want but i can not seem to figure out how to run a script in the new dir

my script that i want to run is in /home/user/bin/script

---

### Post by Ozymandias_117 on 2010-05-16
Are you trying to write a script, to open a terminal, to run a script...? Or am I misunderstanding something?

---

### Post by kaibob on 2010-05-16
The following command opens a terminal window and runs a shell script. The second bash is often but not always necessary to keep the terminal window open after the script is completed. This command assumes that the directory that contains the script is in your path. 

```
gnome-terminal --execute bash -c "scriptname ; bash"
```

I ran a test, and the above command does work with the working-directory option.

---

