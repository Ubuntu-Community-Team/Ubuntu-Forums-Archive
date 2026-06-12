---
title: "Haven't got any root access"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by bkbilly on 2009-12-14
I was messing around with my ubuntu linux and now I have a problem...
I CAN'T DO ANYTHING THAT NEEDS ROOT ACCESS... :(
I know exactly what I did but I don't know how to reverse it...
I opened gnome-terminal and I wrote "**sudo visudo** and I uncommented something that it should disable root password and I commend the last line...
When I try to edit it by typing **sudo visudo** it shows me this message:
> bkbilly is not in the sudoers file.  This incident will be reported.
Can you please help me edit this file to the default?

---

### Post by sisco311 on 2009-12-14
If you are using Ubuntu 9.10 (Karmic Koala), then open a terminal and run:
```
pkexec visudo
```to edit the file.

If not, then boot in the *Recovery Mode* and fix the sudoers file.

[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

### Post by bkbilly on 2009-12-14
That's true! I am using koala...
I will try and I will tell you!
Thanks for your help!

---

### Post by Sef on 2009-12-15
Moved to ABT

---

### Post by bkbilly on 2009-12-15
IT WORKS!!! 
thanks for your help!!!! :)

---

### Post by sisco311 on 2009-12-15
> **bkbilly said:**
> IT WORKS!!! 
thanks for your help!!!! :)

You are welcome!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

EDIT: Thanks!

---

