---
title: "How to copy a file to usr/lib"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by inearlygaveup on 2009-03-03
How do I copy a file to usr/lib as shown, when I try I get "Error While Moving - Details Permission Denied. Using Ubuntu 8.10

file called libfmodex.so.4.* that has to be copied to your library folder (usually /usr/lib).

Trying to install YamiPod

---

### Post by cet' on 2009-03-03
You mean you want to copy libfmodex.so.4.* into usr/lib

try 
 
 sudo cp libfmodex.so.4.* /usr/lib

---

### Post by ClaytonOT on 2009-03-03
sudo cp filename path

---

### Post by Michelangelo1973 on 2009-03-03
I had a similar problemo since the sys don't allow me to copy a file to the /home dir (arguing "i don't have the permission") I use sudo -i 
then cp -r /home/myfolder/Desktop/you name it  /home/you name it
and another thing i learn today Linux IS Case SENSITIVE
be careful on the Uppercases

---

### Post by inearlygaveup on 2009-03-03
> **cet' said:**
> You mean you want to copy libfmodex.so.4.* into usr/lib

try 
 
 sudo cp libfmodex.so.4.* /usr/lib

Sorry its libfmodex.so.4.02.05 

Do I enter sudo cp libfmodex.so.4.02.05 in the terminal

---

### Post by swoody on 2009-03-03
You can also use:
```
gksu natilus
```
to open Nautilus in sudo mode. Then navigate to the /usr/lib folder with that window, and can just drag-and-drop the file from your Desktop into /usr/lib

---

### Post by cet' on 2009-03-03
> **inearlygaveup said:**
> Sorry its libfmodex.so.4.02.05 

Do I enter sudo cp libfmodex.so.4.02.05 in the terminal

yes ... assuming you'r working directory is currently where the file is. otherwise give the full path

if libfmodex.so.4.02.05 is on your home folder you would do 

 sudo cp /home/inearlygaveup/libfmodex.so.4.02.05 /usr/lib

---

### Post by inearlygaveup on 2009-03-03
What do you mean by working directory, the package is on my desktop

---

### Post by swoody on 2009-03-03
The 'working directory' is the location that you're in at any given time in the Terminal. So if you enter 
```
cd /home/*yourname*/Pictures
```
then your current working directory would be the Pictures folder. Get it? :)

Anywho... in you case, since your file is on your desktop, you will need to enter this to change your 'working directory' to your Desktop.:
```
cd /home/*yourname*/Desktop
```
...and then to copy the file to /usr/lib:
```
sudo cp libfmodex.so.4.02.05 /usr/lib
```
Or you can use this command by itself to accomplish the same thing without having to change directories:
```
sudo cp /home/*yourname*/Desktop/libfmodex.so.4.02.05 /usr/lib
```
This tells the 'copy' command where to find the file, so you don't have to change directories, and show 'copy' where the file is.

Is that clear? Or did I just muddy things up? :) Either one will work. Try it out, and let us know how it works out for you :)

---

### Post by inearlygaveup on 2009-03-03
Thanks.....I think I understand,I will give it a go later I'm in Windows at the moment.
I would love to get to grips with Linux but am finding it slow going.

How is "Jaunty Jackalope" then is there much change, will it be easier for a beginners 
9:50pm

---

### Post by ClaytonOT on 2009-03-03
Don't give up too quick, it just takes repetition. Go around make files on your desktop, move them to other directories, copy them, delete them, etc, etc....

Just make sure you use your terminal wherever you can, otherwise you won't learn how to use it. It may be simpler for you right now to drag and drop that file useing nautilus, but what would you learn? 

What woody86 said, WILL work.

Friendly tip:

When you're ~$ you can access your /home/username/ directories by simply typing "cd Documents" or "cd Desktop" (whatever lays inside your username)

If you decide to rename the file make sure the extensions are intact.

---

### Post by inearlygaveup on 2009-03-03
Thanks for your encouragement..........I will keep trying. Thank goodness for this forum.

---

### Post by swoody on 2009-03-03
It's no problem, glad I could help :)

Linux is actually quite simple once you understand it's build, and your options. Just as learning anything new, there will be a bit of learning involved, but it's not going to be as tough as you think. Then one day you will step back and take a breath, and have an "Ah ha!" moment where it all clicks. It's kind of like switching to the metric system, it might seem foreign and strange at first, but once you comprehend it, it's much simpler and easier to use than you would have ever thought!

For some great reading, and to learn more about Ubuntu and Linux in general, check out the two links for beginners in my signature. They've helped me out a TON in the past!

Jaunty is still a ways from being completed, so as to say whether or not it'll be more functional for beginners, I cannot say for sure. The user interface and ease of use are always being improved upon, and one of the main goals of the developers, so  I'm sure it's going to be a great release :)

When you get on Ubuntu, take a swing at the commands I posted above, and let us know how it works out, and if you encounter any difficulties :D

---

