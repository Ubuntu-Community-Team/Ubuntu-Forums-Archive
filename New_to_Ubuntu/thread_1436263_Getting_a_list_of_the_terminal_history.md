---
title: "Getting a list of the terminal history?"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by RED666 on 2010-03-22
How can get a list of the history of the commands I entered in terminal? Would be handy for a newb like me...

---

### Post by blur xc on 2010-03-22
check this out-
```
history
```

---

### Post by r-senior on 2010-03-22
$ history

Some Unix commands are more obvious than others! :D

You can go back to a command in the history using:

$ !<number>

---

### Post by Paqman on 2010-03-22
Up and down arrows will scroll back though previous commands. Typing:```
history
```
...will list all commands. You might want to limit that to the last 20, which would be:
```
history 20
```

---

### Post by natravis on 2010-03-22
and finally, if you use ```
history >> history.txt
``` you can get the last 500 (or less, if you use history XX where XX is a number) commands, in a text file and then open it in nano, or gedit, or whatever your heart desires.

---

### Post by RED666 on 2010-03-22
Thx, how can I write it to a file (or get it to Gedit)?

---

### Post by RED666 on 2010-03-22
Thanks!

---

