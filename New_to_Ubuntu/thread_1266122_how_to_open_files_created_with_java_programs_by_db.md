---
title: "how to open files created with java programs by dbl click"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by DrScum on 2009-09-14
I have just switched from XP to ubuntu on my laptop. With java applications such as Gantt Project and Visual Understanding Environment I used to be able to open filed created by these programs by double clicking. In Ubuntu that doesn't work. I have to start the program first and then open the file from within the program. I hope that's just because I don't know how to do it right.

Can anyone point out to me what I was missing so far?

---

### Post by sunchiqua on 2009-09-14
You should be able to launch it by double-click upon adding execute permission.

```
sudo chmod +x /home/user/application.jar

```

---

### Post by DrScum on 2009-09-14
the execute permission to the file I want to open or to the java application?

For Gantt Project, there is no Gantt Prorject.jar but a Gantt Project.sh

---

### Post by sunchiqua on 2009-09-14
Then change the permissions ( + execute ) to the shell script. Unless it's executable, you'll not be able to use double-click.

---

### Post by DrScum on 2009-09-14
Meanwhile I tried it but it didn't work. neither with the application VUE.jar nor with ganntproject.sh

---

### Post by ashwinhgtx on 2009-09-14
Right click the file>Properties and tick the executable checkbox in the permissions tab. Then see if you get an Open With option. Over there select Sun Java or whatever you have.

---

### Post by DrScum on 2009-09-14
Did that, upon clicking you get a window with options "Run in Terminal", "Display", "Cancel", "Run". Neither run option has any consequences. Display displays the java source text, cancel obviously cancels.

---

### Post by ashwinhgtx on 2009-09-14
> **DrScum said:**
> Did that, upon clicking you get a window with options "Run in Terminal", "Display", "Cancel", "Run". Neither run option has any consequences. Display displays the java source text, cancel obviously cancels.

Try it with the .jar files.

---

