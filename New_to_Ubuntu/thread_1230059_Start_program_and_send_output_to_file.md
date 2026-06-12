---
title: "Start program and send output to file"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by redgar on 2009-08-02
I'm new to bash scripting...started 10 minutes ago. I need to write a simple program to execute a program (the name of the program is 'reset') and then send the output of the program to a file (the name of the output file is 'result'). This is what I've drafted after using the web. I haven't coded the program file yet. Please help. 
 
#!/bin/bash 
echo $PATH 
echo Start of Program
 
#Start program & send output to file
sudo reset & > result.txt
[FONT=Arial][SIZE=2][FONT=Arial][SIZE=2]exit 0[/SIZE][/FONT]
[/SIZE][/FONT]

---

### Post by credobyte on 2009-08-02
```
sudo ./reset > result.txt

```Also, do you really need to use *sudo* ?

---

### Post by llamabr on 2009-08-03
And frankly, not to be obtuse, and I know they hate when I mention man pages around here, but the bash man page has lots of interesting info about this, and the differences and uses of >, >>, |, etc.

---

