---
title: "what is exactly difference between process and thread ?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by atulchavan on 2010-05-25
sorry for very basic question... 
i am not getting clear picture of what is exactly runs on cpu, it is the thread or process. i read a lot of stuffs but not getting clear idea. sometime they use 'task' keyword for thread or process. 
from whatever i read i got "threads are run in the address space of the respective process, it is easy to switch between threads than processes and it is not expensive too" 
if threads are run on the core, how exactly they are run, where can i get complete information of threads. 
can anyone guide me.

---

### Post by obscurant1st on 2010-05-25
I can explain things, but not to the far end. it will be basic.

Process the main application you are running. It may contain threads or may not.
But threads are created by processes or some other threads. It may be created for different different reason. Like from a text editor if you are giving a print, it may start another thread and it may start another process. 
I hope its a little bit clear for you.
I answered this, since i didnt see any reply for you question. You may get better answers.

---

### Post by atulchavan on 2010-05-26
Thank you for your instant reply... somewhat clear .
but what is task. i am reading kernel source code, they are frequently using 'task' keyword. whether task=?process or task=?thread

---

