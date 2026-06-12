---
title: "[SOLVED] How to install *.bin file?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by sudeepk on 2008-12-18
I have downloaded google earth installation file which is in "bin" format. can any one tell me how to install a bin file?

---

### Post by donkyhotay on 2008-12-18
A *.bin is a binary file (the linux equivalent of a *.exe on windows). All you need to do is make certain you have execute permissions and run it.

---

### Post by sudeepk on 2008-12-18
i have write permission.. but when i double click on it, its asking me to choose a program to run!
is there any way to run it?

---

### Post by binbash on 2008-12-18
run it via ./asdasd.bin or sudo ./asdasd.bin

---

### Post by SuperSonic4 on 2008-12-18
> **binbash said:**
> run it via ./asdasd.bin or sudo ./asdasd.bin

You'll need to cd to the directory first, so if it's on the desktop

```
cd ~/Desktop
./asdasd.bin 
```

---

### Post by Duck2006 on 2008-12-18
In the terminal type,

sh GoogleEarthlinux.bin

[http://earth.google.com/support/bin/answer.py?hl=en-ch&answer=44713](http://earth.google.com/support/bin/answer.py?hl=en-ch&answer=44713)

---

### Post by Duck2006 on 2008-12-18
Don't forget to cd to where the file is.
ie cd ~/Desktop

---

### Post by Perfect Storm on 2008-12-18
You can get Goggleearth through synaptic or add/remove if you use medibuntu;
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by oldos2er on 2008-12-18
> **sudeepk said:**
> I have downloaded google earth installation file which is in "bin" format. can any one tell me how to install a bin file?

 Run these commands one at a time, in a terminal:

 cd Desktop

 chmod a+x GoogleEarthLinux.bin

 sudo ./GoogleEarthLinux.bin

 After the installer finishes, and asks you if you want to start the program, choose Quit.

---

### Post by decoherence on 2008-12-18
right-click on the file and select Open with Other Application

in the box that comes up, click the triangle beside "Use a custom command" and type "sh" in to the text field (no quotes) and hit open.

There really should be an easier way to do this. Even if I set execute permissions, I still get the error that there is no program available to open it.

Still, I think I win for 'n00b ease of use' ;) Anyone got an easier way? (aside from adding medibuntu)

---

### Post by donkyhotay on 2008-12-18
There are 3 permissions each file has, read permission (ability to view the file), write permission (ability to make changes to the file) and execute permission (ability to 'run' a file). What everyone said previously to run the program is correct if your doing this through the CLI (which is a good idea, if something goes wrong the CLI is where your error messages appear) but if you want the GUI method:

right click on the file
select properties
click on the permissions tab
checkmark the 'allow executing file as program' located near the bottom
double-click on the file
if it asks you if you want to open or run it select run

---

### Post by decoherence on 2008-12-18
> 
checkmark the 'allow executing file as program' located near the bottom
double-click on the file
if it asks you if you want to open or run it select run

that was the first thing i tried but i still got the same error and no option to run the program... i think it's a bug because what you describe is definitely the way it should work.

---

