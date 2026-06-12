---
title: "How can I install visual c++ 2005 express?"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by Tapas Bose, India on 2009-09-19
Hallo everybody.
I have a cd of visual c++ 2005 express edition. Is there any way to install visual c++ 2005 in my Ubuntu 9.04?
Thanks in advance.

---

### Post by NoaHall on 2009-09-19
Nope, as far as I can remember, it doesn't work with wine. However, I use my 2008 and 2010 beta through Virtual Box running windows.

---

### Post by Hosmion on 2009-09-19
> **NoaHall said:**
> Nope, as far as I can remember, it doesn't work with wine. However, I use my 2008 and 2010 beta through Virtual Box running windows.

Why wouldn't it work with Wine?

---

### Post by Tapas Bose, India on 2009-09-19
> **NoaHall said:**
> Nope, as far as I can remember, it doesn't work with wine. However, I use my 2008 and 2010 beta through Virtual Box running windows.
Okay. When I execute the command 
sh ./winetricks
A window open where I saw the entry vc2005trial and vc2005express. What are this?

---

### Post by NoaHall on 2009-09-19
Those are the runtimes, not the IDE.

---

### Post by Tapas Bose, India on 2009-09-19
> **NoaHall said:**
> Those are the runtimes, not the IDE.
Thank you. Can I install Borland C++ 5.02 or any other compiler?

---

### Post by NoaHall on 2009-09-19
There are plenty on Linux. Look up gcc

---

### Post by Tapas Bose, India on 2009-09-19
Thanks for reply. I can use gcc. But GUI based compiler is needed for my student. She is not accustomed in Linux.

---

### Post by sunchiqua on 2009-09-19
Try Geany ( of course, don't forget to install build-essential package ) - simple yet powerful :)

---

### Post by shae on 2009-09-19
Code::Blocks would be a good idea.  It is cross platform and also has a wxgui builder: [http://www.codeblocks.org/](http://www.codeblocks.org/).

Also consider Netbeans.  It can of course do Java, but it also has a C/C++ plugin.

---

### Post by Tapas Bose, India on 2009-09-20
> **sunchiqua said:**
> Try Geany ( of course, don't forget to install build-essential package ) - simple yet powerful :)
Thanks. I googled and found Geany. Can you tell my how to install build-essential? I searched synaptic, there I found build-essential is installed in my computer. Some day before I had installed gcc.

---

### Post by pcjunkie on 2009-09-20
SCite has compiler and its very sleek...

---

### Post by sandyd on 2009-09-20
vc2005express

IS visual c express.

see screenshot

---

### Post by NoaHall on 2009-09-20
It's not the IDE. Different things.

---

### Post by sandyd on 2009-09-20
aww man.
it INCLUDES the IDE
says so if you click the next button.

except that i just closed it.
running it again...

---

### Post by NoaHall on 2009-09-20
It doesn't.

---

### Post by sandyd on 2009-09-20
how much do you wanna bet
<see screenshot>
then what in the whole wide world is circled in the screenshot if itsnot the IDE.

---

### Post by sunchiqua on 2009-09-20
> It's not the IDE. Different things. 	

Visual C++ 2005/2008 are IDE's, packed with a compiler, not "different things".

---

### Post by Funnnny on 2009-09-20
For C/C++ in Linux, I can suggest.
First, build-essential for gcc and other things for advance ( like makefile ) later. 
Second, if you need an IDE, try Eclipse ( my favorite ), Code::Blocks ( good IDE with WxWidget ), NetBeans, Kdevelop ( it's good if you use KDE instead of Gnome ).
You can still use gedit ( nice if you have some plugins ), emacs ( many old people use it ), try to write a simple makefile ( a simple makefile is really...simple :P ).

---

### Post by NoaHall on 2009-09-20
Very well then, but it doesn't work well, and I don't think you're talking about the one installed via winetricks.

there is a the RUNTIME, and the IDE. They are different things. The IDE is for making things, the runtime is for running things.

---

### Post by sandyd on 2009-09-20
that is the one in winetricks
there are two different things. vc2005 is the libraries. vc2005express is the IDE & stuff

---

### Post by camper365 on 2009-09-20
There is also the Anjuta IDE and it is GTK based. It requires g++ to be installed (which is part of build-essential).
I haven't used it much, but I have noticed that it automatically makes the AUTHORS, COPYING, etc. files. It looks nice for Linux development.

---

### Post by Funnnny on 2009-09-20
Arr, just forgot about Anjuta, it's nice if you're using Gnome, and want a light weight IDE.

---

### Post by Tapas Bose, India on 2009-09-20
> **carlee said:**
> vc2005express

IS visual c express.

see screenshot
Hallo. Can you tell me how to install it? Just executing  sh ./winetricks
 command?

---

### Post by Funnnny on 2009-09-20
./winetricks vc2005express , i think so.
But it's not recommend to use VC under Wine

---

### Post by Tapas Bose, India on 2009-09-20
> **Funnnny said:**
> ./winetricks vc2005express , i think so.
But it's not recommend to use VC under Wine
Thanks. Can you please tell me why it  is not recommended? Is it hazardous for my machine?

---

### Post by Funnnny on 2009-09-20
So...does VC Express compile program that can run under Linux ? No
It's native ? No
It's using GCC ? No
So why not drop it and use some other native IDE ?

---

### Post by sandyd on 2009-09-20
> **Tapas Bose, India said:**
> Thanks. Can you please tell me why it  is not recommended? Is it hazardous for my machine?

I just took it out for a test drive.
Not good performacnce and some thing or another is making it extremely crashy.

scrape that from your list of options.

---

### Post by Tapas Bose, India on 2009-09-21
Good morning.
Thank you both of you Funnnny & carlee.

---

