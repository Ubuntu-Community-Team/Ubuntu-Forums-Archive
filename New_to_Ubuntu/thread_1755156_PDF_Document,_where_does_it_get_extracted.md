---
title: "PDF Document, where does it get extracted?"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-10
Hi there folks, I clicked on a link, then it wanted me to extract the file, and I do not know where it ended up.  Can't I put the file where I want to, i.e., desktop, home folder, etc?

---

### Post by dwhite on 2011-05-10
that's a great book, i learned a lot from it and have a copy at my desk.

it is probably in your downloads folder in your home directory, that is the default for most browsers so unless you changed it that is where it should be,

yes you can put the document anywhere you want it, drag and drop, or with the terminal, or nautilus

here is a screenshot of me dragging a file from my downloads folder to my document folder

---

### Post by dcsoldschool53 on 2011-05-10
> **TAspr said:**
> Hi there folks, I clicked on a link, then it wanted me to extract the file, and I do not know where it ended up.  Can't I put the file where I want to, i.e., desktop, home folder, etc?

Yes you can extract it to any where you want it. Click extract. It will open up a directory. Across the top, you will see your user name and the folder it can be extracted in.

 If you look on the side panel, you will see a list of directories that you can click on. If you want it to be extracted to your Desktop, click on the side panel where you see the word Desktop; then, click extract at the bottom. This will place it on your Desktop.

---

### Post by Dondermans on 2011-05-11
For those prompted to take a look: the guide is available for free download:

[http://ubuntupocketguide.com/download_main.html](http://ubuntupocketguide.com/download_main.html)

---

### Post by TAspr on 2011-05-11
Folks, thank you for all your help!  Much appreciated.  I am getting to like the latest Ubuntu more and more as I use it.  I am not sure if I can do things as easy with it, as sometimes it uses a command line, trial and error, but it is a nice operating system.

---

### Post by TAspr on 2011-05-11
> **dwhite said:**
> that's a great book, i learned a lot from it and have a copy at my desk.

it is probably in your downloads folder in your home directory, that is the default for most browsers so unless you changed it that is where it should be,

yes you can put the document anywhere you want it, drag and drop, or with the terminal, or nautilus

here is a screenshot of me dragging a file from my downloads folder to my document folder


Hi there, where is the programs that you mentioned, "*with the terminal, or nautilus*"

---

### Post by dwhite on 2011-05-11
> **TAspr said:**
> Hi there, where is the programs that you mentioned, "*with the terminal, or nautilus*"

hi, you can get to the terminal by pushing the Ubuntu/Windows key (or clicking on the Applications icon in the launcher bar) and typing "terminal" in the search area (if you are going to use it much right click on the icon in the launcher after it loads and and click "keep in launcher")

now to use the terminal you have to know some commands to move files, create files, rename files etc.  in fact i think that is one of the things the Ubuntu Pocket Guide and Reference by K. Thomas book does really well (see chapter 5 "hands-on the command-line), here is a list of commands  [http://ss64.com/bash/](http://ss64.com/bash/)  but to start just follow along with the Pocket Guide

alot of the time you will find it easier to use the nautilus file manager, if you just click on the home icon in Unity the nautilus file manager opens and shows the contents of your home folder and you can quickly move around the file system using  your mouse

to see the difference open a terminal and type ```
ls
```this will give you a list of what's in your home folder.  now if you click on the home icon in the launcher you see the same folders/files just in a graphical format rather than a list

ps i'm not sure what version of Ubuntu you are using in what i've wrote i've assumed 11.04 with Unity but maybe i'm mistaken?

---

### Post by TAspr on 2011-05-11
> **dwhite said:**
> hi, you can get to the terminal by pushing the Ubuntu/Windows key (or clicking on the Applications icon in the launcher bar) and typing "terminal" in the search area (if you are going to use it much right click on the icon in the launcher after it loads and and click "keep in launcher")

now to use the terminal you have to know some commands to move files, create files, rename files etc.  in fact i think that is one of the things the Ubuntu Pocket Guide and Reference by K. Thomas book does really well (see chapter 5 "hands-on the command-line), here is a list of commands  [http://ss64.com/bash/](http://ss64.com/bash/)  but to start just follow along with the Pocket Guide

alot of the time you will find it easier to use the nautilus file manager, if you just click on the home icon in Unity the nautilus file manager opens and shows the contents of your home folder and you can quickly move around the file system using  your mouse

to see the difference open a terminal and type ```
ls
```this will give you a list of what's in your home folder.  now if you click on the home icon in the launcher you see the same folders/files just in a graphical format rather than a list

ps i'm not sure what version of Ubuntu you are using in what i've wrote i've assumed 11.04 with Unity but maybe i'm mistaken?


Yes, correct, version 11.04.  Now, when I clicked on "Applications" and did a search, and right-clicked on the *(if you are going to use it much right click on the icon in the launcher after it loads and and click "keep in launcher*"), it does not give me an option to add it to the launcher.  It does nothing as a matter of fact.

By the way, thank you for a clear presentation of these steps, I appreciate it.

---

### Post by dwhite on 2011-05-11
> **TAspr said:**
> Yes, correct, version 11.04.  Now, when I clicked on "Applications" and did a search, and right-clicked on the *(if you are going to use it much right click on the icon in the launcher after it loads and and click "keep in launcher*"), it does not give me an option to add it to the launcher.  It does nothing as a matter of fact.




sorry first left click on it in the search window to load it, once it loads an icon will show up in the launcher panel, now right click the panel icon and add to launcher

---

### Post by TAspr on 2011-05-11
> **dwhite said:**
> sorry first left click on it in the search window to load it, once it loads an icon will show up in the launcher panel, now right click the panel icon and add to launcher

Ok, I am sorry, I do not mean to be a difficult person to deal with, but first, I click on "Applications" then launch the program, then right click on the icon and add it to the launcher?  Is this the correct way to do this?

---

### Post by dwhite on 2011-05-11
> **TAspr said:**
> Ok, I am sorry, I do not mean to be a difficult person to deal with, but first, I click on "Applications" then launch the program, then right click on the icon and add it to the launcher?  Is this the correct way to do this?

no worries :)  , yes this sounds right


[LIST]
[*]when you say "launch the program" that means left click on the icon when it shows up in the "Applications" window
[*]Now once the terminal application is running an icon will appear in the launcher
[*]right click on the icon in the launcher and select "Keep in Launcher"
[*]now even when you quit the terminal program an icon will remain in the launcher and you can click on this at anytime to start the terminal program
[/LIST]
here's a better way


[LIST]
[*]do a search and find the terminal, now just click and drag the icon to the launcher and it will stay in the launcher., i'll attach a screen shot.
[/LIST]

---

### Post by TAspr on 2011-05-11
> **dwhite said:**
> no worries :)  , yes this sounds right


[LIST]
[*]when you say "launch the program" that means left click on the icon when it shows up in the "Applications" window
[*]Now once the terminal application is running an icon will appear in the launcher
[*]right click on the icon in the launcher and select "Keep in Launcher"
[*]now even when you quit the terminal program an icon will remain in the launcher and you can click on this at anytime to start the terminal program
[/LIST]
here's a better way


[LIST]
[*]do a search and find the terminal, now just click and drag the icon to the launcher and it will stay in the launcher., i'll attach a screen shot.
[/LIST]


How Awesome!  Thanks so much.

---

