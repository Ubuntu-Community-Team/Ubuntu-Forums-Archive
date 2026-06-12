---
title: "Ubuntu Questions relating to user/PathVariable/terminal"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by zawmai on 2010-09-02
1) What is a root user? Is it like the windows version of the "administrator?" I only have one user on my laptop with ubuntu, so does that make me the root user?

2) How can I make a Path Variable? I recently installed Java SE JDK and wants to make it to my appleviewer located in home/username/jdk1.6.0_21/bin/appletviewer.

3)Where can I learn how to use the terminal? Is it useful at all?

---

### Post by carl4926 on 2010-09-02
You should not login as root
Only as user
> I only have one user on my laptop with ubuntu, so does that make me the root user?No

You get admin rights by using 'sudo' in a terminal
Eg; sudo apt-get update

---

### Post by cariboo on 2010-09-02
> **zawmai said:**
> 1) What is a root user? Is it like the windows version of the "administrator?" I only have one user on my laptop with ubuntu, so does that make me the root user?

The root user is similar to the administrator in Windows. Your user account is simialr to a standard user account, escept that you can have admin priviledges using sudo for command line commands, or gksu fro grahical commands.

> 2) How can I make a Path Variable? I recently installed Java SE JDK and wants to make it to my appleviewer located in home/username/jdk1.6.0_21/bin/appletviewer.


You shouldn't have to set a path for programs in your home directory

> 3)Where can I learn how to use the terminal? Is it useful at all?

Have a look [here]("https://help.ubuntu.com/community/UsingTheTerminal") for a basic run down on using a terminal.

---

### Post by rhythmiccycle on 2010-09-02
> **zawmai said:**
> 
1) What is a root user? Is it like the windows version of the "administrator?" 

in a sense root is like administrator, but i'm sure not everyone will agree due so some details that I'm not aware of.


sometimes you need to be a root user to run certain operations that could potentially harm your pc, such as installing stuff and and accessing certain directories. 

you never really need to login as a root user, you just need to use the "sudo" command when running certain commands in the terminal. 

on occasion I use the "gksudo nautilus" command to open a window with root privileges, (i.e. no restrictions)

> **zawmai said:**
> 
1) I only have one user on my laptop with ubuntu, so does that make me the root user?


you are not really a root user, but your root password will be the same as your user password.


> **zawmai said:**
> 
2) How can I make a Path Variable? I recently installed Java SE JDK and wants to make it to my appleviewer located in home/username/jdk1.6.0_21/bin/appletviewer.

I'm not sure what you mean here, sorry. 

if you want to make a new directory you can  just right click a blank part of a window, or under the edit menu, click "new folder" 

if you want to make a shortcut of a folder or file, right click on it and select "make link"

you can also do the same operations from the terminal. using the "ln -s" command

> **zawmai said:**
> 
3)Where can I learn how to use the terminal?


in my opinion if you really want to get good at using the terminal try using "INX"

[http://inx.maincontent.net/](http://inx.maincontent.net/)

is a boot disk, and runs a prompt only Linux O.S. and in contains a bunch of very helpful tutorials. I knew nothing about terminals, and after doing the tutorials on INX, i now feel pretty comfortable there. 

you can also ask question on this forum.

> **zawmai said:**
> 
3) Is it useful at all?


the terminal is very useful. I use it all the time.

 for example, I can use the terminal to make additional monitor resolutions, it can make "virtual" ones that are not supported by the video card, but run fine.  my tv's vga's optimal resolution is 1360x768, but that was not an option in the monitor settings. I used the terminal to make that into a working option. 

that is just one of the many times the terminal has been very useful to me

---

### Post by zawmai on 2010-09-02
Thanks you guys for the information! 
> 2) How can I make a Path Variable? I recently installed Java SE JDK and  wants to make it to my appleviewer located in  home/username/jdk1.6.0_21/bin/appletviewer.The reason why I asked this question was because:
-When I was using windows, I used a software called  Eclipse to write Java(I'm a total noob)
-In order for Eclipse to work in windows, I had to go to the environment varaible to make a  "Path" variable.

---

### Post by carl4926 on 2010-09-02
Don't try and compare Windows with Linux
You might as well compare Dog Turd with Luxury Chocolate.

Taste and see how good Linux is

---

### Post by zawmai on 2010-09-02
> **carl4926 said:**
> Don't try and compare Windows with Linux
You might as well compare Dog Turd with Luxury Chocolate.

Taste and see how good Linux is

I didn't mean to offend you and Linux. One of the reason why I picked Linux is because I heard a lot of great things about it. Don't get me wrong. Even thought I'm still a windows user, I'm open or *Ubuntu* to Linux. I'm thrilled to use Linux and explore it. Bottom line is I want to use Eclipse to write Java on Ubuntu, but every time I try to open Eclipse, it shows me this error: 

[CENTER][CENTER]**A Java Runtime Environment (JRE) or Java Development Kit (JDK)**
**must be available in order to run Eclipse. No Java virtual machine**
**was found after searching the following locations:**
**/home/zawmai/Desktop/eclipse/jre/bin/java**
**java in your current PATH**
[/CENTER]
[LEFT]
[/LEFT]
 [/CENTER]

---

### Post by rhythmiccycle on 2010-09-02
> **zawmai said:**
>  Bottom line is I want to use Eclipse to write Java on Ubuntu, but every time I try to open Eclipse, it shows me this error: 
....


i just installed Eclipse to check it out. and its running fine, I didn't do anything special. just installed from software center, and then run it. 

do you have java installed? when you type "java" into the software center is there a green check mark on the "openJDK java runtime 6" icon?? if not try seeing if installing that fixes the problem.

I added a screenshot to show you.

---

### Post by zawmai on 2010-09-02
> **rhythmiccycle said:**
> i just installed Eclipse to check it out. and its running fine, I didn't do anything special. just installed from software center, and then run it. 

do you have java installed? when you type "java" into the software center is there a green check mark on the "openJDK java runtime 6" icon?? if not try seeing if installing that fixes the problem.

I added a screenshot to show you.

Oh Wow. Thnx. I just installed "OpenJDK Java 6 Runtime," and Eclipse worked perfectly fine.

---

### Post by rhythmiccycle on 2010-09-03
I'm glad you got it working.

somethings work a little different on ubuntu vs windows, but if the main thing you want to do is write java. I think you'll eventually like ubuntu better.

---

