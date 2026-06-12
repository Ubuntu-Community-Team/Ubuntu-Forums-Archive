---
title: "Where are applications installed?"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by j moon on 2010-07-22
I am used to Windows XP but I have just installed Ubuntu Netbook 10.04 on my wife's netbook. She wanted a cross-stitch programme so I googled and found kxstitch. I downloaded it (possibly from SourceForge?) and it appeared as a folder named kxstitch-0.8.4 in a download folder. I clicked on it and found an archive: kxstitch-0.8.4tar.gz
 
I opened the archive and found 22 objects. I opened some of them(eg readme & INSTALL) and gleaned the impression that I needed more programming skills than I possess in order to run this application!
 
I went to the Ubuntu Software Centre and found kxstitch there so I pressed the install button. Everything went well but I cannot find where it is installed unless it is the identical application that is in the download folder.
 
Can anybody help with simple instructions on getting this application to work?

---

### Post by wojox on 2010-07-22
Try and reboot to see if it shows up in your Menu. If not open your terminal and type

```
kxstitch
```

---

### Post by new__buntu on 2010-07-22
> **j moon said:**
> I am used to Windows XP but I have just installed Ubuntu Netbook 10.04 on my wife's netbook. She wanted a cross-stitch programme so I googled and found kxstitch. I downloaded it (possibly from SourceForge?) and it appeared as a folder named kxstitch-0.8.4 in a download folder. I clicked on it and found an archive: kxstitch-0.8.4tar.gz
 
I opened the archive and found 22 objects. I opened some of them(eg readme & INSTALL) and gleaned the impression that I needed more programming skills than I possess in order to run this application!
 
I went to the Ubuntu Software Centre and found kxstitch there so I pressed the install button. Everything went well but I cannot find where it is installed unless it is the identical application that is in the download folder.
 
Can anybody help with simple instructions on getting this application to work?

The software center should not have left you with just a tar file, so that's not it. If you need to verify you installation try running ```
kxstitch
``` in terminal (that may not be the package's exact name, so some [tab-completion]("http://ubuntuforums.org/showpost.php?p=399109&postcount=4") might me necessary).

Also, most applications will put themselves somewhere in the Applications tab at the top left of your screen, so you might want to double check that it's not already there, it might have stuck itself somewhere unexpected.

---

### Post by techunit on 2010-07-22
Installing applications is very simple in Ubuntu... Go to the software center and search for it then click install, right? wrong... you need to make sure that it has a graphical user interface (GUI) go to the software center and search cross stitch program... What is a cross stitch (I am thinking panorama or something) also you installed an application for kubuntu... while this isn't a problem you should try only to install things designed for the gnome desktop environment if you can, you will get better performance. I hope this helps. the program you installed probably needs to be launched from the terminal...

Open the terminal and type ```
kxstitch
``` really hope this helps...

Perhaps I can help you find a better option...

---

### Post by Paqman on 2010-07-22
> **j moon said:**
> 
I went to the Ubuntu Software Centre and found kxstitch there so I pressed the install button. Everything went well but I cannot find where it is installed unless it is the identical application that is in the download folder.

This is the way to go, you should always get your software through the package manager if you can. Downloading stuff from random websites is a pain.

As far as I can tell, kxstitch is a graphical app, so should have created a menu item when it installed. If it's really not lurking in a menu, try opening a terminal and launching it with:
```
kxstitch
```
and see what the system says.

---

### Post by j moon on 2010-07-22
Thanks for the replies. Cross stitch is a form of embroidery used to create pictures on fabric.
 
Several answers are telling me to use a terminal. Where or what is that? I cannot find that anywhere.
 
Have read the help menu and went to the synaptic package manager. Found kxstitch listed, marked for reinstallation and applied. Still cannot find any sign of this application. Very frustrating!

---

### Post by wojox on 2010-07-22
Alt+F2

```
gnome-terminal
```

---

### Post by carniola on 2010-07-22
You can also find the Terminal under the Applications Menu --> Accessories --> Terminal

Have you checked in the accessories menu? Or maybe under the office menu? Maybe graphics?

---

### Post by kerry_s on 2010-07-22
kxstitch is a kde program, netbook is more of a gnome based. most kde programs are set not to show in gnome menu.

so open your file manager(files & folders)
on the left click "file system"
click on: usr-> share-> applications
look for the program & double click

you can add it to the main menu manually if it's there & works.

---

### Post by Paqman on 2010-07-22
> **j moon said:**
> 
Several answers are telling me to use a terminal. Where or what is that? I cannot find that anywhere.


On the netbook remix it's under Accesories. If you can get it run through the terminal or by following kerry_s's instructions then you can add a launcher to your menus by going to System > Main Menu and entering a new item. You might have to rummage around to find a nice icon for it, the default one is a bit naff.

---

### Post by j moon on 2010-07-22
It is now working! Many thanks to all. Went to Alt-F2, typed in kxstitch and it opened like magic. I just hope it all works for my wife.
 
Thanks again.

---

