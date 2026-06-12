---
title: "Beagle"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by groeswenphil on 2009-01-29
Hi,
Let me get this right. I've installed Beagle and deskbar-applet to help me search for lost files.

I have two hard disks fitted to my computer.....main disk holds Ubuntu and Windows duel boot...........and lots of my work files are in the Windows area.

I also have a second hard drive from an old computer.

Beagle is now running and it looks as though it is cataloguing my files....but will it catalogue Windows areas and my old drive?

Phil

---

### Post by minsf on 2009-01-29
please forgive my silly question, but why not searching for the files with "find" from the CLI?

---

### Post by NeuralEskimo on 2009-01-29
groeswenphil,

I'm not a beagle user; however, all of the search engines have a configuration tool which allows you to tell the search engine which directories to index. For beagle, there is a commandline tool (beagle-config) and a graphical tool (beagle-settings). Again, not being a beagle user, the configuration tool should appear in System Menu under Preferences. If you do not see it there, open a terminal and type "beagle-settings" and press enter.

Sorry I can't be of more help, but this should get you started. Good luck.

---

### Post by clueless on 2009-01-29
I am not sure if Beagle indexes NTFS partitions. Anyway, by default it indexes only your home folder. You can add whatever folder you want it to index, by going to the "preferences" menu (under Search in the main window) and then at the 2nd tab.

-- edit --

As NeuralEskimo said, running beagle-settings from the terminal will work just as well

---

### Post by groeswenphil on 2009-01-29
Thanks everybody...........Terminal method worked.

What does this mean?
"find" from the CLI?

Sorry if I sound stupid.

Phil

---

### Post by clueless on 2009-01-29
You can run the command on the terminal:
find something

to find a file or folder named "something". It is not like beagle however. Beagle searches within the files and gives you the results. With find you already have to know what is the name of the file or folder in order to search it.

---

### Post by minsf on 2009-01-30
> **groeswenphil said:**
> What does this mean?
"find" from the CLI?

i meant the Command Line Interface. sorry, i should've been more clear.

i guess one can also search inside files with grep, but the advantage of beagle must be in the indexing which happens when cpu is free. and it can probably access ntfs easier. am i right? 
sorry... i'm just a newbie wondering if i need beagle.

---

### Post by NeuralEskimo on 2009-01-30
> **minsf said:**
> i guess one can also search inside files with grep, but the advantage of beagle must be in the indexing which happens when cpu is free. and it can probably access ntfs easier. am i right? 
sorry... i'm just a newbie wondering if i need beagle.

You are correct. Beagle and its competitors index the content of each file when you install. Then as you add and remove files, Beagle, et al. updates its index. It's Google for your hard drive. In fact, Google Desktop is available for Linux. Of course, there is also Tracker and Strigi. That is, there are a number of search engines which will index your files. However, these programs do far more than index your hard drive, they can also index your email, calendar, etc. As a result, you can search all of your personal data and the program for a specific key word or keywords.

---

### Post by minsf on 2009-01-30
cool, thanks!

---

