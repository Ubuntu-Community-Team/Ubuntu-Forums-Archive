---
title: "Command Line Basics"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by Neoncamouflage on 2011-06-11
One of the reasons I like Ubuntu/Linux more than Windows is that a lot of what you can do either requires or is made far simpler by using the terminal. I just enjoy using it far more than pretty much any GUI, like I've touched Synaptic maybe once, really disliked the setup, and have happily been using apt-get for everything I've needed. So now I've wound up with two questions.

1. This is probably incredibly stupid or simple, but in every ubuntu basics or commands guide I've read, and through all google searches, I can't for the life of me figure out how to simply run a program. I don't really want to type in the command every time I want to open a browser or something, but just the fact that I don't know how to select a specific program and run it from the command line is killing me. 

2. I've been looking for a really good guide or list of commands for Ubuntu 10.04, which is what I'm using. Everything I've found simply tells about the same set of basic commands that I've read a dozen times over(ls, cd, cp, rm, apt-get...etc), I just want like a giant list of commands and what they all do, so I can skim through and look at. Does anyone know of such a thing?

---

### Post by wildmanne39 on 2011-06-11
> **Neoncamouflage said:**
> One of the reasons I like Ubuntu/Linux more than Windows is that a lot of what you can do either requires or is made far simpler by using the terminal. I just enjoy using it far more than pretty much any GUI, like I've touched Synaptic maybe once, really disliked the setup, and have happily been using apt-get for everything I've needed. So now I've wound up with two questions.

1. This is probably incredibly stupid or simple, but in every ubuntu basics or commands guide I've read, and through all google searches, I can't for the life of me figure out how to simply run a program. I don't really want to type in the command every time I want to open a browser or something, but just the fact that I don't know how to select a specific program and run it from the command line is killing me. 

2. I've been looking for a really good guide or list of commands for Ubuntu 10.04, which is what I'm using. Everything I've found simply tells about the same set of basic commands that I've read a dozen times over(ls, cd, cp, rm, apt-get...etc), I just want like a giant list of commands and what they all do, so I can skim through and look at. Does anyone know of such a thing?
Hi, I do not know of one like what you are asking about, but I bought a ubuntu book called toolbox with over 1000 commands from amazon.com and it comes in very handy.

---

### Post by wolfen69 on 2011-06-11
If you wanted to open firefox, just type firefox. Or, you could do alt-F2 and type the name of the app.

---

### Post by Neoncamouflage on 2011-06-11
> **wolfen69 said:**
> If you wanted to open firefox, just type firefox. Or, you could do alt-F2 and type the name of the app.

Just type the name.....wow.... How I never even thought of trying that I have no idea.

---

### Post by conradin on 2011-06-11
Most any command guide will work. if you goto the terminal and type 
$firefox [www.google.com](www.google.com)
a firefox browser session will appear.
alternatively, if you type:```
firefox https://help.ubuntu.com/community/UsingTheTerminal &
```
a browser with a basic walk through for the terminal will appear.
the trick is to realize the commands are programs or scripts, and depending on what you want to do, you can link the programs input and output together in nearly any way you can imagine.

---

### Post by dcsoldschool53 on 2011-06-11
> **Neoncamouflage said:**
> One of the reasons I like Ubuntu/Linux more than Windows is that a lot of what you can do either requires or is made far simpler by using the terminal. I just enjoy using it far more than pretty much any GUI, like I've touched Synaptic maybe once, really disliked the setup, and have happily been using apt-get for everything I've needed. So now I've wound up with two questions.

1. This is probably incredibly stupid or simple, but in every ubuntu basics or commands guide I've read, and through all google searches, I can't for the life of me figure out how to simply run a program. I don't really want to type in the command every time I want to open a browser or something, but just the fact that I don't know how to select a specific program and run it from the command line is killing me. 

2. I've been looking for a really good guide or list of commands for Ubuntu 10.04, which is what I'm using. Everything I've found simply tells about the same set of basic commands that I've read a dozen times over(ls, cd, cp, rm, apt-get...etc), I just want like a giant list of commands and what they all do, so I can skim through and look at. Does anyone know of such a thing?

Anytime I want to find a command to open any application, I first look on my computer. In a terminal, I type```
alacarte
```When the main menu opens, I search for any program that I want to find the command to and click on it. Then, I click on properties. A pop up box will open, and I look for the```
Command:
``` that I can type in to the terminal. For example, open office command is```
ooffice
```Here are two books that you might be interested in.[http://www.amazon.com/Practical-Guide-Ubuntu-Linux-3rd/dp/013254248X/ref=sr_1_7?s=books&ie=UTF8&qid=1307851164&sr=1-7](http://www.amazon.com/Practical-Guide-Ubuntu-Linux-3rd/dp/013254248X/ref=sr_1_7?s=books&ie=UTF8&qid=1307851164&sr=1-7) and [http://www.amazon.com/Linux-Command-Shell-Scripting-Second/dp/1118004426/ref=pd_sim_b_7](http://www.amazon.com/Linux-Command-Shell-Scripting-Second/dp/1118004426/ref=pd_sim_b_7)Hope this will help you.

---

### Post by nzjethro on 2011-06-12
> **dcsoldschool53 said:**
> Anytime I want to find a command to open any application, I first look on my computer. In a terminal, I type```
alacarte
```When the main menu opens, I search for any program that I want to find the command to and click on it. Then, I click on properties. A pop up box will open, and I look for the```
Command:
``` that I can type in to the terminal.

Wow, that's useful. I've got the regularly used programmes down, but whenever I need a less oft-used one I normally have to trawl through /usr/bin. This is a lot easier!

Oh, and OP, check out the link in this thread.
[http://ubuntuforums.org/showthread.php?t=61464](http://ubuntuforums.org/showthread.php?t=61464)

---

