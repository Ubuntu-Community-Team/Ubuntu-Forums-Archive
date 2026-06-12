---
title: "i am missing something using Putty"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by iwannalearn on 2009-07-15
Hi, i am using ubuntu-server

i have a program i use. and to run it i change to the directory where it is then i do

$ ./program_name

and i can see it running fine.

only thing when i exit putty the prog stops running.

so how can i exit putty with out closing the prog? 

thanks

---

### Post by iwannalearn on 2009-07-15
just found this and will give it a shot.

# nohup my_program &

any comments on this please?

thanks

---

### Post by Zenze on 2009-07-15
I guess its stopping because you are ending your session on that system when you exit putty, therefore ending all your running processes? IDK just a guess really.

You may want to try running it in the background by putting a '&' at the end of your line. But it would still be 'your' process so it may still end when you exit putting.

EDIT: Yea you found it before I posted.

---

