---
title: "why the terminal"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by gokul2411s on 2010-01-05
Hi everybody.

I recently installed Ubuntu after facing a lot of problems. But I feel proud I got through somehow and also learnt a bit if Unix. But I have one constant doubt lingering in my mind. Please do not be offended in any way.

I want to know what is the purpose of the terminal. If everything can be done in GUI mode, what is the purpose of the terminal. I ask this because I have been a Windows user till now. In Windows, as you all know, everything is done in the GUI. I don't remember the last time I use the DOS terminal.

Why should I use one in Ubuntu? Once again, if this instigates you I am sorry. But I genuinely want to know.

Thanks and a belated happy new year.

---

### Post by bodhi.zazen on 2010-01-05
Geeks don't let geeks drive gui apps :p

Some people prefer the terminal and, unlike windows, teh terminal and bash commands are quite helpful.

Other then that, what do yo uuse when your graphical interface breaks -> terminal.

Sometimes it is much easier to type a command then search through gui and gui menues.

Sometimes graphical apps do not have all the options available on the command line.

And finally, when managing servers, one is often editing config files, which are in plain text, and a terminal is as easy as a gui.

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Temposs on 2010-01-05
There is a trade-off in use of the terminal versus GUI tools. 

You can do things more quickly in the terminal, if you know what you're doing. Everything is accessible from commands on a simple program(the terminal), rather than having to open multiple potentially heavy applications and sorting through menus and such. Having everything doable from a terminal command makes anything scriptable, which is very useful for combining functionality of different applications.

The downside to using the terminal is the learning curve. If you don't know any commands to start with, and you're just presented with a terminal prompt, there's not really a good way to do useful things. You have to memorize at least a core number of commands and their options, in order to be efficient at the command line.

---

### Post by blur xc on 2010-01-05
There are a million things you can do in the terminal that still can't be done so easily or at all in the gui (don't ask me to list them).

Linux comes with MANY GUIs, to do some action is different between Gnome, KDE, *boxes, etc., but is always the same in the terminal.

It's easier to have someone copy/past a command in termianl than to explain the same steps in the gui- example, to install ubuntu-restricted-extras

Terminal-
sudo apt-get install ubuntu-restricted-extras 

Gui (In gnome, it'll be differnt in kde)- pulldown applictaions menu- select add/remove programs, search for ubuntu restricted extra, check mark the box, click apply, etc....  (recalling from memory, and I don't remember when the last time I used add/remove so forgive any errrors)...

Do show a list of partitions on your hdd-
sudo fdisk -l

Easy cheesy, to get the same info from the gui someone else will have to chime in, I don't know it...

BM

---

### Post by Captain_tux on 2010-01-05
It's also a fact that there are things you can do in the terminal that you simply cannot do with a GUI...

---

### Post by MooPi on 2010-01-05
After you become accustomed to using the terminal, other methods seem clumsy and slow. Generally terminal commands and usage cut straight to the detail making more precise config and customization possible. As an example lets look at a nice program Rhythmbox. With this application you can listen to all your music and rip your CD's to ogg, flac, mp3 etc. The preferences give you the option to change how you would like to do these things. Now from command line I can do all these thing but my options can be more specific and detailed. I can change what I want each time I rip a CD much quicker and efficiently. GUI's tend to give bland choices or standard choices and with terminal the sky is the limit. To it's detriment the terminal can be a flood of info as well. My experience with man pages for mencoder as an example.

---

### Post by KeLa on 2010-01-05
If you started to use computer with the CP/M or DOS period you did everything in "terminal" meaning no gui and if you can do it in terminal the why bother to do it in gui :)
Terminal is more powerful than gui.

Here is one examle command:
find ~/test/ -type f ! -name "*.*" -exec rename -v 's/$/\.txt/' {} \;
That will rename all files in directory test under your home directory so that if it has no extension it will add .txt to it.
That's one you can't do in gui.

---

### Post by gradinaruvasile on 2010-01-05
You see, the graphical Linux server (X server) is just another process that runs on top of the shell (text mode) environment. It is not like in Windows where everything has a graphical tool, because there the graphical UI (along with the single user mode that to this day causes many security problems) was the starting point of development. Their Command Prompt is not nearly as powerful as the Terminal in Linux (i did not use PowerShell, so i cannot comment of its efficiency), although i use it on Windows too because its really useful.

And its a really powerful toy to play with. With the newer Linuxes around, there might be that most (mostly basic) tasks can be accomplished by the GUI but having the terminal commands around is a big help for those that can use it.
Its is the heart of a Linux operating system administration. You can configure almost anything with it - except some very graphical apps. It gives you access to the powerful low level Linux commands that dont have Windows equivalents, manipulate raw data etc. And you can create/debug new scripts. Also, some tasks can be accomplished faster (such as updating the system), some, like compiling and some configuration programs, are terminal-only commands. It also provides a unified "language" for all linux flavours (not everything, but most  basic  and advanced commands are the same or very similar). It is also very useful for remote administration without having to interfere with the user using the graphical environment (no need for grabbing the display to play with remote desktop) export the X server via ssh etc.
Also it is a very good debugging tool.

---

### Post by KeLa on 2010-01-05
And if you need more examples why to use terminal please take a look at this page
[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)
That is good guide how to edit files from command line in batch mode.

---

### Post by Methuselah on 2010-01-05
The forums is biased towards terminal commands because it is very easy to communicate them in this text medium.
Telling someone how to navigate through a gui is more prone to wordiness and musinderstanding than telling them to copy/paste a command in the terminal.
Also, when they need to post the output back it is far easier for them to do so from terminal output than gui (screen capture and upload file?).

Additionally, terminal commands and command line apps are far easier to automate.
Sure you can browse through the software center and install the programs you want but if you have done a clean Ubuntu install it is far easier to run a script that installs everything you want while you sleep.

The Linux community also leans more towards knowledge of your computer.
Proprietary OS makers earn their keep by making you dependent on them to make everything 'easy' without you having to know anything.
While Ubuntu is a very newbie friendly community and distribution it still is expected that people will eventually become comfortable with the tools.
So other posters don't attempt to hide the terminal but more consider it as something everyone can come to grips with at least to some extent.

The only real disadvantage the terminal has is that functionality is not quite as easy to discover as browsing through a GUI.
However, since it is used very commonly in the linux world new users quickly pick up a few commands and learn where to look for more information (manpages).

I could say more but my post is already long enough.
Windows and OSX still have their terminals so it is not strictly a DOS thing.
However the terminal has a higher standing in linux culture one could say.
The terminal commands are more 'standard' than any particular graphical interface.

---

### Post by blur xc on 2010-01-05
Just a side note- I've been on the phone w/ tech support a few times regarding windows software (not MS), and many times their first instruction is -> super-R (widows key + R) to bring up the run dialog, and enter cmd ad hit enter to bring up a dos prompt.

It's not just a *nix thing, it's just that *nix does it a lot better than DOS.

BM

---

### Post by lswb on 2010-01-05
Imagine ordering your lunch at a delicatessen. You tell the counter person that you want a "hot pastrami on rye with swiss cheese and mustard, and a coke"

Now imagine that instead of just saying what you want, you have to use some kind of touch screen where you select the type of bread, select the meat, check off any condiments, then navigate to the "beverage" menu and select that. 

It is simply faster to just state what you want, (if you know how) then to use a gui menu for many tasks.

---

### Post by Cheesemill on 2010-01-05
Check out this thread from earlier today:
[http://ubuntuforums.org/showthread.php?t=1372778](http://ubuntuforums.org/showthread.php?t=1372778)

---

### Post by theozzlives on 2010-01-05
If you looked at Windows through a technician's eyes, you'd see there's still a lot to be said about the "DOS" prompt. Some stuff you can't do with a GUI. Linux is a lot more powerful and I like that it's modular (seperate from GUI). One day I'll be as proficient as I used to be in DOS.

---

### Post by gabo.cr on 2010-01-05
I had a problem once with the GUI, it was not working right.
I was able to fix it with Terminal.
I also had a problem with the Ubuntu Software Center, I was not able to open it and install anything, I was able to fix it with Terminal, without Terminal, I would be in trouble !

---

