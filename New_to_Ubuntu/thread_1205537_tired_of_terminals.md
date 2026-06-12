---
title: "tired of terminals"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by cyber.creed on 2009-07-06
hello all, i am guna skip the big long speach about how noobish i am and get to the point, 

(what i am trying to do)
i have a line of code that i need to enter in the terminal in order to bypass some system requirements and i would like to use that line as an application so i can either double click it on my desktop or better yet put it in the list of start up applications so that i dont have to copy and paste it in the terminal everytime i log in

(right direction>?)
i read something in another thread about useing the Launcher to achive something along these lines but in tinkering with it i cant seem to figure it out 

any help or advice would be great, thanx ;)

---

### Post by s.fox on 2009-07-06
Hi and welcome to the forum,

Take a look [here]("http://www.howtogeek.com/howto/ubuntu/how-to-add-a-program-to-the-ubuntu-startup-list-after-login/"). :D

-Silver Fox

---

### Post by frunns on 2009-07-06
Create a file, enter #!/bin/bash as the first line, the command you want to run as the second line. Then run
```
chmod +x <file>
```
Now you have a executable file! Or if you want it as a startup application you can go to System->Preferences->Sessions (something along those lines at least), and just create a new startup application and enter your command as the command it should run (think that should work), but a better solution would be to point it to the executable file you've created.

---

### Post by cyber.creed on 2009-07-06
thank you very much for your help, i managed to get it to turn into a shell script but i am still confused as to what exactly i am suposed to do with the 
chmod +x <file>[FONT=monospace]Part of it[/FONT]

---

### Post by scorp123 on 2009-07-06
> **cyber.creed said:**
>  i am still confused as to what exactly i am suposed to do with the 
chmod +x <file>[FONT=monospace]Part of it[/FONT] Make the file executable. ```
chmod +x /path/to/file
```

---

### Post by ad_267 on 2009-07-06
The "chmod +x" command means modify the file permissions to make it executable. You can also just right click on it and do this from the file properties dialog.

---

### Post by cyber.creed on 2009-07-06
i see no, i got it to work, thank you very much everyone for all of your help

---

