---
title: "python- run a .py file - default action is gedit"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by marshall31415 on 2009-08-29
Hi.

I am used to coding python in windows, and in windows when i double click on any .py file the default action is to execute it through a command like terminal (not IDLE). In Ubuntu however, the default action is to open it with "gedit" text editor. I have created a custom open command to get it to default open with IDLE for editing - but how can I get it to run in a terminal like windows does it when I double click the file.

I want to do this so I can just double click a file that I've made and have it run instantly. I dont want it to run in IDLE as I want it to close upon executing, like windows does.

Thanks

---

### Post by rajeev1204 on 2009-08-29
> **marshall31415 said:**
> Hi.

I am used to coding python in windows, and in windows when i double click on any .py file the default action is to execute it through a command like terminal (not IDLE). In Ubuntu however, the default action is to open it with "gedit" text editor. I have created a custom open command to get it to default open with IDLE for editing - but how can I get it to run in a terminal like windows does it when I double click the file.

I want to do this so I can just double click a file that I've made and have it run instantly. I dont want it to run in IDLE as I want it to close upon executing, like windows does.

Thanks

You can specify x-term to  run it in a terminal by right click the file and open with.

---

### Post by red_spyder on 2009-08-29
If you want to run it through the terminal, you need to install python first. Type:
sudo apt-get install python
insert your password and let it install on its own. If it asks to confirm the download, just type 'y' and hit enter. 
When you get full control of the computer again, go to the directory the .py file is located through the terminal and to execute it type 'python *.py' where * is the name of your file.

---

### Post by Copernicus1234 on 2009-08-29
I dont know how Windows does it, but if you just want to run it instantly when double clicking on it, you can just right click the file, go to Properties, and under the Permissions tab, check "Allow this file to run as a program".

In your python file, add this at the top:

```
#!/usr/bin/env python
```

Now when doubleclicking that file, Linux will know what program to use to run it and it will just run as a ordinary program.

---

### Post by rajeev1204 on 2009-08-29
> **red_spyder said:**
> If you want to run it through the terminal, you need to install python first. Type:
sudo apt-get install python
insert your password and let it install on its own. If it asks to confirm the download, just type 'y' and hit enter. 
When you get full control of the computer again, go to the directory the .py file is located through the terminal and to execute it type 'python *.py' where * is the name of your file.

python is installed by default on all linux distros.

---

### Post by donkyhotay on 2009-08-29
> **Copernicus1234 said:**
> In your python file, add this at the top:

```
#!/usr/bin/env python
```

Now when doubleclicking that file, Linux will know what program to use to run it and it will just run as a ordinary program.

+1 This is the easiest way of doing it IMHO.

---

### Post by marshall31415 on 2009-08-30
> **Copernicus1234 said:**
> I dont know how Windows does it, but if you just want to run it instantly when double clicking on it, you can just right click the file, go to Properties, and under the Permissions tab, check "Allow this file to run as a program".

In your python file, add this at the top:

```
#!/usr/bin/env python
```Now when doubleclicking that file, Linux will know what program to use to run it and it will just run as a ordinary program.

Thanks very much for your help. This worked

Thanks to everyone else who answered too.

---

