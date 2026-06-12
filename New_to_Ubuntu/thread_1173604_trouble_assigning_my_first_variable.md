---
title: "trouble assigning my first variable"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by adamogardner on 2009-05-29
I'm following the book "Linux Cookbook For Everyday Use" and I'm in the assigning variables chapter  I figured I'd assign "name" to my name:  name="adamogardner" but it's not working.  what am I doing wrong.  Here is a brief history in my gnome terminal:  

adamogardner@CRONUS:~$ $name="adamogardner"
bash: =adamogardner: command not found

---

### Post by Volt9000 on 2009-05-29
You only need to use the dollar sign in front of the variable name when accessing its contents, not when assigning. So just do:

```

name="adamogardner"
echo $name

```

---

### Post by Hospadar on 2009-05-29
Not that it super matters in this scenario, but for a single word value like that (no spaces) you don't even really need the quotes (and as all shell variables are saved as strings anyways, numbers don't need any special treatment either)

---

### Post by adamogardner on 2009-05-29
I got it.  Thanks.

---

