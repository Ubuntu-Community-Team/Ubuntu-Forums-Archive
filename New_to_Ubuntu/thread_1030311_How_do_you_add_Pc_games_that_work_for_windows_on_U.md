---
title: "How do you add Pc games that work for windows on Ubuuntu"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by justin p on 2009-01-04
I got a game for my child and do not know ho to install it please help me:

---

### Post by mips on 2009-01-04
First, which game is it?
Secondly you could try using WINE
[http://www.winehq.org/](http://www.winehq.org/)
[http://en.wikipedia.org/wiki/Wine_(software]("http://en.wikipedia.org/wiki/Wine_%28software"))

If the game is not 3D intensive or uses OpenGL instead of DirectX you could install Virtualbox and install WinXP/Vista inside Virtualbox and then install the game in WinXP as you would install it in a normal windows system.
[http://www.virtualbox.org/](http://www.virtualbox.org/)
[http://en.wikipedia.org/wiki/VirtualBox](http://en.wikipedia.org/wiki/VirtualBox)

All the above software is available in the Ubuntu repositories and can be installed via Synaptic or the command line, whichever you prefer.

Dedicatet Ubuntu forum for WINE, [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)
Ubuntu Gamers Arena, [http://gaming.gwos.org/doku.php](http://gaming.gwos.org/doku.php)

---

### Post by jackmetal on 2009-01-04
Hi Justin,

You could go about it a number of ways (depending on the game).  

It's possible that you could install it and run it under wine.  You can install wine from the repositories if you don't already have it installed.  Another option is through running windows in a virtual machine (if the game won't install/play via wine).  You can use any of a number, such as VirtualBox (my personal favorite), VMWare, etc..  

What game are you trying to install?

*EDIT* Doh,  just noticed mips added more info for you!  Sorry for the duplication.  :-)

---

### Post by sadaruwan12 on 2009-01-04
> **justin p said:**
> I got a game for my child and do not know ho to install it please help me:
First of all please tell us what kind of a game is that or give us a name

---

### Post by shadowlands on 2009-01-04
will this work for other products as well, such as adaptive software like Read and write Gold?

---

### Post by jackmetal on 2009-01-04
> **shadowlands said:**
> will this work for other products as well, such as adaptive software like Read and write Gold?

Is that a Windows App?  If so then yes.  Wine will allow you to install/use a lot of Windows Applications/Games, etc.  'Any' other one that will not work under wine, can be used in VirtualBox (or VMWare, etc).  VirtualBox allows you to install your Windows OS (on any other OS) as a Virtual Machine and run it under Linux (and other OS's).

---

### Post by shadowlands on 2009-01-04
My son's game "Tonka Tow" will not work I encounter an error message " cannot find the autorun program"  Can someone help me figure this out?  thanks in advance

---

### Post by jackmetal on 2009-01-04
A couple other options for you (which I neglected to mention previously):

Cedega and Crossover Office.  I've used both with good success also, but now I primarily use VirtualBox or just plain wine.

---

### Post by sadaruwan12 on 2009-01-04
> **shadowlands said:**
> My son's game "Tonka Tow" will not work I encounter an error message " cannot find the autorun program"  Can someone help me figure this out?  thanks in advance
Did you managed to get Wine installed if the answer is yes then did you installed the game correctly.

---

### Post by jackmetal on 2009-01-04
> **shadowlands said:**
> My son's game "Tonka Tow" will not work I encounter an error message " cannot find the autorun program"  Can someone help me figure this out?  thanks in advance

Once you have, install wine: sudo aptitude install wine
Then you can just right click on the setup.exe (or whatever the install filename is) and select open with wine.  Or from a command prompt, change into that directory (or cd) and type wine setup.exe

What command have you used to try to install it thus far?

---

### Post by shadowlands on 2009-01-04
I followed the directions from the wine.org page and I went to add and remove programs and add them. I just used the terminal as you described to install wine and I am trying a new game by " Bright Child interactive and I am still getting the same error message.

---

### Post by shadowlands on 2009-01-04
information  Not sure how to answer this question.  so I am  placing a link for the product in here so I do not give faluty informatiion [http://www.synapse-ada.com/texthelp/read&write_gold/read&write_gold_default.htm](http://www.synapse-ada.com/texthelp/read&write_gold/read&write_gold_default.htm)> **jackmetal said:**
> Is that a Windows App?  If so then yes.  Wine will allow you to install/use a lot of Windows Applications/Games, etc.  'Any' other one that will not work under wine, can be used in VirtualBox (or VMWare, etc).  VirtualBox allows you to install your Windows OS (on any other OS) as a Virtual Machine and run it under Linux (and other OS's).

---

### Post by jackmetal on 2009-01-04
Ok, visited the link you sent.  It looks like that particular software (Read and Write Gold) is Windows only (Vista recommended).  

So, it 'may' work under wine, but it would definitely work with VirtualBox (or any other Virtualization software, such as VMWare).

How did you install wine?  Did you download it via apt (or aptitude) from the Ubuntu repositories or did it install it from the Wine website?

Is the game on CD?  If so, when you install the CD and navigate to it with the filemanager, what happens when you right click on the Setup.exe or Install.exe and select 'open with wine'?

---

### Post by shadowlands on 2009-01-04
question: what do you mean " change into that directory (or cd) and type wine setup.exe"> **jackmetal said:**
> Once you have install wine: sudo aptitude install wine
Then you can just right click on the setup.exe (or whatever the install filename is) and select open with wine.  Or from a command prompt, change into that directory (or cd) and type wine setup.exe

What command have you used to try to install it thus far?

---

### Post by jackmetal on 2009-01-04
> **shadowlands said:**
> question: what do you mean " change into that directory (or cd) and type wine setup.exe"

I'm sorry if I made it sound complicated, I was giving you a couple different options in one reply (a gui method and a command line method).  I typically work command-line, but I know some users prefer gui.

If you prefer to install via command-line: you can open a terminal, cd into the directory where the game is located (or cd to the cdrom directory if it is on CD), then type wine setup.exe (or if it's not named setup.exe, install.exe or whatever it is named).

If you prefer to do it via GUI: Open your filemanager (nautilus in gnome), change into either the directory where the game is downloaded to (or to the cdrrom directory if it's on CD), right click on the install file name (setup.exe, or install.exe, etc.) and select "open with wine".

---

### Post by shadowlands on 2009-01-04
I think I need baby s teps.  I understand only half of it and not sure how ro do theother half. What do you mean by "terminal cd"  the game is on cd, 


The name of the cd is Caillou magic palyhouse  by pbs kids, it id a brighter child interactive learning game.


> **jackmetal said:**
> I'm sorry if I made it sound complicated, I was giving you a couple different options in one reply (a gui method and a command line method).  I typically work command-line, but I know some users prefer gui.

If you prefer to install via command-line: you can open a terminal, cd into the directory where the game is located (or cd to the cdrom directory if it is on CD), then type wine setup.exe (or if it's not named setup.exe, install.exe or whatever it is named).

If you prefer to do it via GUI: Open your filemanager (nautilus in gnome), change into either the directory where the game is downloaded to (or to the cdrrom directory if it's on CD), right click on the install file name (setup.exe, or install.exe, etc.) and select "open with wine".

---

### Post by jackmetal on 2009-01-04
No problem.  We all need baby steps sometimes.  :-)

OK, give me a little information and I'll try my best to walk you through the install as simply as possible.

1) What version of Ubuntu are you running?  
2) Are you using Gnome (or KDE, Xfce,etc)?
3) When you insert the game CD, does your filemanager automatically pop up and display the CD and files located on it?
4) Exactly what process did you use to install Wine?  
5) If you open a command prompt and type the following: wine --version , what version is displayed?

A command prompt will be the terminal.  To open the terminal, go to the menu, then under Accessories select Terminal.

---

### Post by shadowlands on 2009-01-04
I followed the directions on winehq.org.  

I then followed this" Once you have install wine: sudo aptitude install wine"
when I look in to the software sources and click third party it reads that I am using ubuntu hardy


Not sure what the file manger is but when I insert the CD a n icon pops up on the screen of the cd . When I click that icon  an I guess you would callit an application bx pops up and states that this medium contains software intended to be automatically started would you like to run ? "  the soft ware will run  directly from the medium  and there is an cancel button and a run button

I click run  and a error message pops up " cannot find the autorun program

---

### Post by jackmetal on 2009-01-04
Ah, ok..  

Instead of having it autorun, select 'cancel' when that selection comes up.  When you do that, does a filemanager display (showing you the files on the CD)?

---

### Post by jackmetal on 2009-01-04
Here's a page that might help you with installing windows programs in Ubuntu.  It's specifically written for Ubuntu Hardy.

[http://vitalbodies.wordpress.com/2008/07/13/how-to-install-a-windows-program-in-ubuntu-hardy-heron/](http://vitalbodies.wordpress.com/2008/07/13/how-to-install-a-windows-program-in-ubuntu-hardy-heron/)

---

### Post by jackmetal on 2009-01-04
Also, if you haven't checked out the Wine FAQ, it's located:

[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

Specifically, section 3:

3.2. How do I run an installer using Wine?

Double-click on the installer, just like in Windows!

You can also right click on it, choose "Run with", and pick wine.

Or, if all else fails, open a terminal window, "change directory" to the folder containing the installer's .exe file, and run the installer with Wine by typing "wine" followed by the installer's filename. For example:

$ cd Desktop
$ wine FluffyBunnySetup.exe

If the installer's name doesn't end in .exe, you have to say "wine start" and then the filename:

$ cd Desktop
$ wine start FluffyBunnySetup.msi

(Don't type the $, that's the computer's prompt. Instead of typing the entire filename, you can usually type just the first few letters and then press Tab, and the computer will complete the filename you were typing for you.)

3.3. I have an MSI file, how do I install/run it?

MSI files cannot be run directly, you need to use the msiexec program. MSI files can be installed in Wine from the terminal like this

wine msiexec /i whatever.msi

Alternatively:

wine start whatever.msi

That will then run the MSI program the same as if you had double-clicked it in Windows.

---

### Post by shadowlands on 2009-01-04
now I get it when I click on the cd icon the file manger pops up showing me what is on the CD.  the

---

### Post by jackmetal on 2009-01-04
> **shadowlands said:**
> now I get it when I click on the cd icon the file manger pops up showing me what is on the CD.  the

Yep! Great to hear!  Did everything install and work ok for you?

---

### Post by shadowlands on 2009-01-04
Naw, I am still working on it.  I am just glad I understand what you are saying to me. my computer looks nothing like the pictures so I can not follow it.

---

### Post by jackmetal on 2009-01-06
Just thought I'd check in with you to see if everything got installed ok for you?

---

