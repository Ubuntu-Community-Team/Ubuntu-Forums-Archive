---
title: "N00B alert! I need help!!!"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by rabidmedia on 2009-07-14
Hello. I have a few questions. I just started with ubuntu 8.10 not too long ago and, needless to say is much different from windows.
 
My main problem is that I don't have the internet directly connected to the computer that ubuntu is installed on. right now, I'm at the local library typing this. I use a flash drive to get files from the internet to my computer.
 
now, to the questions:
 
1: I found where I can download programs and libs from packages.ubuntu.com. I noticed alot of files and programs require many libs and stuff. is there a way to get one .deb file with a collection of files nessassary for a majority of programs? in other words: Is there an easier way to find the required files for a game or program such a packages containing all required files for it?
 
2: I noticed that alot of programs are in raw source form (.tar .gz and stuff like that...) which are just zip files. I saw several tutorials on how to compile them to a usable state and they don't seem that difficult to do. I just need something "KDE" program to do that. long story short: where can I get this KDE thingamabob and the apropriate documedtation to go with it?
 
3: I would like to learn how to program in ubuntu, mostly to make games. in my previous life with Windows XP I would use Game Maker 6.1 or OHRRPGCE or RPG MAKER 2003 and stuff like that. It's time for me to grow up and use a more sofisticated programing language. What would be the best way to begin learning how to program in ubuntu. I have noticed that most of the source code for the .tar files I've downloaded can be opened and edited in the default text editor. are there any other tools I need.
 
I'm not expecting Large elaborate anwsers for my questions. if someone can point me to a link with tutorials and stuff for these questions I'll greatly appreaciate it! ThanX!

---

### Post by kogger on 2009-07-14
1. Most programs have a built-in list of dependencies that are installed along with the program, so if you install something via apt-get or Synaptic (System->Administration->Synaptic Package Manager), you should be good.

2. KDE isn't a program, it's a desktop. If you're using Ubuntu then odds are you're using Gnome instead of KDE. To make it easier to install programs, look for .deb files. To install those you just need to double-click on them.

3. First, settle on a programming language. I'm not that experienced in game programming, so honestly I'm not sure which one you would want to choose, but you will need to get a very good text editor or IDE if you want to make anything substantial. Using gedit (the default text editor) may not be the best choice.

---

### Post by rabidmedia on 2009-07-14
Thanks!

---

### Post by Tibuda on 2009-07-14
You should read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Ratscallion on 2009-07-14
You said you're not on the net with Ubuntu... To get the best out of the downloads, you really ought to be. Most of the packages at your package resource (packages.ubuntu.com i believe) have the dependencies on the page...

---

### Post by Tibuda on 2009-07-14
> **kogger said:**
> Using gedit (the default text editor) may not be the best choice.

Why not? It got syntax hightlight for the most popular languages, an integrated terminal and support for Makefiles (via the external tools plugins). What else do you need?

---

### Post by Yvan300 on 2009-07-14
Here you could try this site, it gives you all you need in deb files. [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by Tibuda on 2009-07-14
To find out the dependencies, you should check [http://apt.alturl.com/](http://apt.alturl.com/)

---

### Post by ecmatter on 2009-07-14
> **rabidmedia said:**
> 3: I would like to learn how to program in ubuntu, mostly to make games. in my previous life with Windows XP I would use Game Maker 6.1 or OHRRPGCE or RPG MAKER 2003 and stuff like that. It's time for me to grow up and use a more sofisticated programing language. What would be the best way to begin learning how to program in ubuntu. I have noticed that most of the source code for the .tar files I've downloaded can be opened and edited in the default text editor. are there any other tools I need.

I'd start by learning as much as I could about the command line, bash scripting, and linux in general before trying to learn a language.

Here's a couple of oft cited resources:

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

[http://tldp.org/guides.html](http://tldp.org/guides.html) (the Advanced-Bash Scripting Guide, Bash Guide for Beginners, and Introduction to Linux guides are all worth a look)

---

### Post by Ratscallion on 2009-07-15
+1

---

### Post by jerome1232 on 2009-07-15
Perhaps AptonCD would be good for you. It can put packages and their dependencies, and the dependencies dependencies all on cd so you don't have to go through dependency hell. (at least I think it can do that for you)

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by ramnarayan on 2009-07-15
> **jerome1232 said:**
> Perhpas AptonCD would be good for you. It can put packages and their dependencies, and the dependencies dependencies all on cd so you don't have to go through dependency hell. (at least I think it can do that for you)

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Second that, this is probably the most useful

another thing you can do is find some one close to your (or someone who can send it to you) and get hold of the entire repository of Ubuntu (6 DVD
's worth) once you get hold of that then you can install almost everything without the net and without worrying about dependencies. And the only thing you need to do is occassionally take you machine to some place where there is good net connectivity and update.

Post these updates you can save the changed configuration using apt-on - which are really useful when you want to reinstall your system.

ram

---

### Post by alexlafreniere on 2009-07-15
> **rabidmedia said:**
> 
 
3: I would like to learn how to program in ubuntu, mostly to make games. in my previous life with Windows XP I would use Game Maker 6.1 or OHRRPGCE or RPG MAKER 2003 and stuff like that. It's time for me to grow up and use a more sofisticated programing language. What would be the best way to begin learning how to program in ubuntu. I have noticed that most of the source code for the .tar files I've downloaded can be opened and edited in the default text editor. are there any other tools I need.
 


C++ is the language to learn for games. Dreamincode.net has great resources for learning C++ and game programming, and forums where you can ask for help when you get stuck. 

[http://www.dreamincode.net/](http://www.dreamincode.net/)

Learn the basic syntax first, then an open source graphics library like OpenGL.

---

### Post by Cheesemill on 2009-07-15
Check out [Keryx]("http://keryxproject.org/") for updating and installing programs on an off-line machine.

---

### Post by rabidmedia on 2009-07-15
I like this... it's pretty cool! Thanx!

---

### Post by rabidmedia on 2009-07-15
Oh my god!!!!! Must....have..............Do...you know anyone who has this? I would like to get it or if there is a mail order service to get these DVDs?

---

