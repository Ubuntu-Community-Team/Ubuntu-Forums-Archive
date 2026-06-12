---
title: "working directory question"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by TCMGO on 2011-04-13
[COLOR=black][SIZE=2]I[COLOR=black] am now starting the tedious process of trying to connect my serial hardware modem to the Internet. I downloaded scanmodem to my USB thumb drive. Now I am [/COLOR][COLOR=black]to: "[/COLOR][COLOR=blue][FONT=Times New Roman][FONT=Verdana][COLOR=red][COLOR=black]use[/COLOR] [COLOR=black]the Linux command **cp** to copy the file scanModem.gz from the USB device to your Linux working directory." I assume my working directory is the root directory I created. Is there a subdirectory I am to use? How do I use the command CP to copy the file into working directory? After completing this step, I am to: [/COLOR][/COLOR][/FONT][/FONT][/COLOR][/SIZE][/COLOR]
 
 
[COLOR=black][COLOR=blue][FONT=Times New Roman][FONT=Verdana][COLOR=red][COLOR=black][COLOR=black][FONT=Verdana][SIZE=2]Enter the following Linux commands:[/SIZE][/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3][COLOR=black]**gunzip scanModem.gz**[/COLOR][/SIZE][/FONT]
**[FONT=Times New Roman][SIZE=3][COLOR=black]chmod +x scanModem[/COLOR][/SIZE][/FONT]**
**[FONT=Times New Roman][SIZE=3][COLOR=black]./scanModem[/COLOR][/SIZE][/FONT]**

[SIZE=2]Is there a terminal function that is used for this? How do I do this?[/SIZE]
[SIZE=2][/SIZE] 

[SIZE=2]It's obvious by my total lack of knowledge that I need to find an "Idiot's guide to Ubuntu" and read it. Is there one?[/SIZE][/COLOR][/COLOR][/FONT][/FONT][/COLOR][/COLOR]

---

### Post by rosencrantz on 2011-04-13
Hi TCMGO,
you can find out your working directory by typing pwd and change directories with cd.
the cp command works with
cp sourcefile targetdirectory
You can enter the three other commands into the terminal exactly as written, if you are in the same directory as the .gz file.
Here's a list of common Linux shell commands.
[http://ss64.com/bash/](http://ss64.com/bash/)
Most help stuff on the web is more reference than general tutorials, but you can check
[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)
[ubuntuguide.org](ubuntuguide.org)
[vic.gedris.org/Manual-ShellIntro/1.2/ShellIntro.pdf](vic.gedris.org/Manual-ShellIntro/1.2/ShellIntro.pdf)
or borrow a book. No recommendations, there, sorry. Lots of us learn Linux by osmosis ;-)

Cheers, rosencrantz

---

### Post by sanderd17 on 2011-04-13
[http://linuxcommand.org/](http://linuxcommand.org/)

Check this site, the first part really helpfull for all basic terminal things.

---

### Post by alphacrucis2 on 2011-04-13
> **TCMGO said:**
> [COLOR=black][SIZE=2]I[COLOR=black] am now starting the tedious process of trying to connect my serial hardware modem to the Internet. I downloaded scanmodem to my USB thumb drive. Now I am [/COLOR][COLOR=black]to: "[/COLOR][COLOR=blue][FONT=Times New Roman][FONT=Verdana][COLOR=red][COLOR=black]use[/COLOR] [COLOR=black]the Linux command **cp** to copy the file scanModem.gz from the USB device to your Linux working directory." I assume my working directory is the root directory I created. Is there a subdirectory I am to use? How do I use the command CP to copy the file into working directory? After completing this step, I am to: [/COLOR][/COLOR][/FONT][/FONT][/COLOR][/SIZE][/COLOR]
 
 
[COLOR=black][COLOR=blue][FONT=Times New Roman][FONT=Verdana][COLOR=red][COLOR=black][COLOR=black][FONT=Verdana][SIZE=2]Enter the following Linux commands:[/SIZE][/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3][COLOR=black]**gunzip scanModem.gz**[/COLOR][/SIZE][/FONT]
**[FONT=Times New Roman][SIZE=3][COLOR=black]chmod +x scanModem[/COLOR][/SIZE][/FONT]**
**[FONT=Times New Roman][SIZE=3][COLOR=black]./scanModem[/COLOR][/SIZE][/FONT]**

[SIZE=2]Is there a terminal function that is used for this? How do I do this?[/SIZE]
[SIZE=2][/SIZE] 

[SIZE=2]It's obvious by my total lack of knowledge that I need to find an "Idiot's guide to Ubuntu" and read it. Is there one?[/SIZE][/COLOR][/COLOR][/FONT][/FONT][/COLOR][/COLOR]

The "working directory" is just where ever your terminal shell thinks is the current directory. To change it you use the cd (change directory) command. For example suppose I had created a directory called somefiles under /home/myusercode. To make the directory somefiles the working directory you issue the following command:

```
cd /home/<myusercode>/somefiles
```

Then to copy your scanModem.gz file from usb flash to somefiles
```
cp /media/<whatever usb flash mounted as>/scanModem.gz scanModem.gz
```

To find out what name the usb flash mounted as just type

ls /media

Once the file is copied just paste the three command you listed into the terminal window.

Edit. Just wondering if you don't know how to get into a terminal. You can start one via the menu Applications - Accessories - Terminal.

---

### Post by TCMGO on 2011-04-13
[SIZE=2]I thank you all for your prompt, useful replies. I have commenced to educate myself. I do have a question: In installing Ubuntu (10.4 LTS) I set up a root partition where I believe Ubuntu installed itself. I created it large enough so that I could also install other Linux programs here. I also created a home partition for my documents, settings, and files, to be kept separate from the OS and installed programs. Am I wrong to beleive that should the need for me to reinstall Ubuntu that my settings files for the OS, as well as documents and data files, kept in the home partition will be left intact upon a reinstall? Also, should I create a file in the root partition (directory?) called programs where I can install Linux programs? Will these programs be affected by an OS reinstall? My thinking is to install modenscan here. [/SIZE]

---

### Post by sanderd17 on 2011-04-13
> **TCMGO said:**
> I thank you all for your prompt, useful replies. I have commenced to educate myself. I do have a question: In installing Ubuntu (10.4 LTS) I set up a root partition where I believe Ubuntu installed itself. I created it large enough so that I could also install other Linux programs here. I also created a home partition for my documents, settings, and files, to be kept separate from the OS and installed programs. Am I wrong to beleive that should the need for me to reinstall Ubuntu that my settings files for the OS, as well as documents and data files, kept in the home partition will be left intact upon a reinstall? Also, should I create a file in the root partition (directory?) called programs where I can install Linux programs? Will these programs be affected by an OS reinstall? My thinking is to install modenscan here. 

When you reinstall ubuntu, you can select to use that partition as your home partition WITHOUT formating it, if you do that, all your files and settings will be intact.

And to install programs, always look in the ubuntu software center or in synaptic. They will do the work for you. If the program isn't in the USC or synaptic (which is very rare), you will have to follow specific instructions for that program (usually in some readme file or notes on some forum or wiki). There is no point in creating a file "programs" now.

Programs you install in ubuntu will be removed when you reinstall. This is normal since an ubuntu upgrade equals a software upgrade of all programs. You can not keep old software with a new ubuntu. If you do an upgrade via the update manager, all software will be pushed to the new version.

If you upgrade by reinstalling, all software will be removed, but there are tools to export your configuration to a script so that you can install all the software you had in your fresh install. The settings of the software will be intact though. So if you reinstall chromium, all your passwords and bookmarks will be there since they are stored in your home partition.

---

