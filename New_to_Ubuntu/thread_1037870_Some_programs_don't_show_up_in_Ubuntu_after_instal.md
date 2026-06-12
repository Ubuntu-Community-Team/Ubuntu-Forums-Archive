---
title: "Some programs don't show up in Ubuntu after installation"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by h2o4444 on 2009-01-12
Hello,
 I'm sort of new to Ubuntu. I've tried 5.04 and 6.06 LTS before and lately I decided to install 8.10 on my HP Compaq tc4200 tablet notebook as a second boot option to the Windows XP Pro Tablet Edition.
 I've been playing with the latest release for almost a week now and I still can't get everything I want to work.
 I installed some programs from the Synaptic Package Manager and they are no where to be found. These programs are Gournal, qbrew, and cycle. I read that there's another program in addition to Gournal for the tablet called Jarnal but I can't find that in the Synaptic Package Manager. I did find Xournal and after it was installed I could access it through Applications > Accessories. I just don't understand why Gournal, qbrew, and cycle won't show up. There might be other applications that I installed and didn't show up but I just remember these three.
 Any help is appreciated, thanks in advance.

---

### Post by RobsterUK on 2009-01-12
I'm not sure specifically about the programs you mentioned, but generally the best way to install software is via Applications > Add/Remove. That way they will show up on the menu system and I think its generally tidier anyway.

---

### Post by ugm6hr on 2009-01-12
It does depend on how those applications are packaged in the repository as to whether they create a menu entry.

If you are certain they are GUI applications (I don't know them), try launching from Terminal. e.g.
```
gournal
cycle
qbrew
```

If that doesn't work, it may give you a help page on how the application launches.

If it gives a "command not found" response, try looking in /usr/bin for any package that has a name similar.

You can also use Terminal to try and "fill in the gaps" with the Tab key -
```
cyc <press Tab key>
```

---

### Post by h2o4444 on 2009-01-12
These programs are not in the Add/Remove.

- Gournal is a "Note taking application for non-windows platforms"
- qbrew is "a recipe calculator for homebrewed beers. It uses Qt for creating its graphical user interface and provides facilities for creating own beer recipes. It even has a manual describing how to brew your first beer yourself!"
- cycle is a "calendar program for women
Cycle is a calendar for women. Given a cycle length or statistics for
several periods, it can calculate the days until menstruation, the days
of "safe" sex, the fertile period, and the days to ovulations, and
define the d.o.b. of a child. It allows the user to write notes and
helps to supervise the administration of hormonal contraceptive tablets."

Add/Remove does not show all the programs installed. Synaptic Package Manager has more programs. Also if you want to install KDE to get Kubuntu you would do it in Synaptic. It seems that these two, Add/Remove and Synaptic, don't work well as they should. That is to say if I install one program in Synaptic, it might not show up in Add/Remove, which is my case with these three programs.

---

### Post by aninaiian on 2009-01-12
Just a quick tip...

The way I usually solve this is to look at the list of installed files for the package (right-click the package in Synaptic, go to properties, go to the installed files tab).
As ugm6hr noted, the command you have to type into the terminal is usually in /usr/bin/.
So, the command your looking for will most likely look like /usr/bin/**somethingthatresemblespackagename** (just type the bold part).

---

### Post by h2o4444 on 2009-01-12
Hello ugm6hr,
 These are all GUI programs and I went in the /usr/bin directory and I found all three of the programs. Gournal and cycle are both script files (perl and python) so they first ran in the terminal and then the GUI showed up. qbrew was an executable, so I was surprised that it did not show up under Applications.
 Anyways thank you for all your help. I'm also new to the terminal and thanks for the quick tutorial!

---

### Post by ugm6hr on 2009-01-12
If you would like them to appear in the menu, you can add them manually.  Or add a panel entry for them.

If you use Gnome: System -> Preferences -> Main Menu

If not - create a .desktop file manually: [http://ubuntu-lxde.wikidot.com/menu](http://ubuntu-lxde.wikidot.com/menu)

---

### Post by h2o4444 on 2009-01-12
Hello aninaiian,
 Thank you for the tip. I will remember that the next time I install something from Synaptic. Now I have a follow-up question: is there a way to create a shortcut of these programs. I tried to move the icon but I get "Error moving file: Permission denied". And when I right clicked on the icon there doesn't seem to be an option to create a shortcut.

---

### Post by h2o4444 on 2009-01-12
Thank you ugm6hr!

---

### Post by oldos2er on 2009-01-12
> **h2o4444 said:**
> Hello aninaiian,
 Thank you for the tip. I will remember that the next time I install something from Synaptic. Now I have a follow-up question: is there a way to create a shortcut of these programs. I tried to move the icon but I get "Error moving file: Permission denied". And when I right clicked on the icon there doesn't seem to be an option to create a shortcut.

 Assuming you're using Gnome, right-click on an empty spot on your desktop, click 'Create Launcher. Next to 'Command' type in /usr/bin/whatever.

---

### Post by h2o4444 on 2009-01-12
Cool. That's a good way to make a shortcut on the desktop. I'll remember that.

---

### Post by angerbill on 2009-05-23
Thanks , I had LMMS installed but couldn't get it to open. Thanks to the above replies, it is on my main menu and I have learned more about my system ! Peace !!

---

