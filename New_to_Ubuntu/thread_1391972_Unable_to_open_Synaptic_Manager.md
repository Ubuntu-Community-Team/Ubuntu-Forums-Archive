---
title: "Unable to open Synaptic Manager"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by gregarion on 2010-01-27
Hey guy, i am unable to open my synaptic manager at all. even at terminal level. what is the problem?


and when i tried to install apt-get install gdb


for some reason, they told me that i am not at root? which is weird because i am the only user and according to 9.10, we are unable to access root? w

---

### Post by hhlp on 2010-01-27
open a terminal aplication - accesories - terminal and execute 

```
gksudo synaptic
```

and give us what you get

the other thinks you must put sudo after the command

```
sudo apt-get install gdb
```

---

### Post by gregarion on 2010-01-27
When i tried doing that, nothing happened in the terminal. it tried to run the synaptic and then it closed and the terminal ended the process.

---

### Post by gregarion on 2010-01-27
and for sudo apt-get install gdb

Reading package lists... Done
Segmentation faulty tree... 50%


that is the output i got and then it ended.

---

### Post by gregarion on 2010-01-27
guys i really need some help in this pls/.

---

### Post by hhlp on 2010-01-27
there is a problem with APT :
> 
>    /var/cache/apt/*.bin

 > the solution is simple: 
 >
 >    # sudo apt-get update
 >
 > if htta don't work, you can do:
 >
 >    # sudo rm /var/cache/apt/*.bin
 >    # sudo apt-get update

---

### Post by gregarion on 2010-01-27
Thanks! , but for the synaptic manager and update manager , both seem to unable to open properly. why is the reason?>

---

