---
title: "Problem with using Wine - No AA jokes please"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by Shumway on 2009-02-27
I'm very new to Linux and am trying to get my Windows Genealogy program, Legacy to work in my Hefty Heron Dual Boot computer.  When I attempt to use Wine, I click Browse C\Drive and on the resulting screen, two folders, Program Files and Windows show. Then I double-click the Program Files folder and in the next screen two more folders show: Common Files and Internet Explorer. That's it. 
I have dozens of Program files folders. so why am I shown only the mentioned two?
Am I not supposed to be finding my Legacy's .EXE file?
Maybe I have configured Wine incorrectly.  
Also, I know nothing about command line computing.
Hope someone can help.
Shum

---

### Post by Ripose on 2009-02-27
That C: drive you are browsing does not actually exist!! It is a"fake folder" created by wine.
To install to Wine you will have to either copy the windows install program to Ubuntu, or insert your CD, or mount the windows partition.

You have to find the install .msi or .exe and RIGHT-Click on it, from the pop-up menu select "Install using Wine".

---

### Post by JoshuaRL on 2009-02-27
And just as a side note, Wine can be used from the command line too.  Just use the "change directory" command below to move to where you have your windows installer files saved:
```

cd /home/user/installers

```
Then, use wine to launch your file:
```

wine installer.exe

```
That way, if it doesn't work or has errors, you can figure out how to fix it.  Also, you can use the "list" command to make sure you're typing it in right.  Like so:
```

ls

```

---

### Post by halovivek on 2009-02-27
wine is a program which is use to run some windows programs in linux. but not all. install the program which you are looking under the wine and you can run. please post the errors are result for more help.

---

### Post by jespdj on 2009-02-27
> **Ripose said:**
> That C: drive you are browsing does not actually exist!! It is a"fake folder" created by wine.
Indeed; to make it more clear: the C: drive that you see in Wine is NOT the C: drive of your Windows partition. It's Wine's own fake C: drive.

You'll have to install that Windows program in your Wine installation - you can't directly access your Windows partition from Wine.

---

### Post by halovivek on 2009-02-27
you can find the list of applications which will run under wine [here.]("http://appdb.winehq.org/")

---

### Post by Shumway on 2009-02-27
Thank you all, Halovivek, jespdj and JoshuaRL, I couldn't make it work so I downloaded another, though lesser genealogy app and opened it nicely with Wine.
Thanks again
Shumway

---

### Post by StephenG on 2009-07-30
This thread comes closest to my issue.  I, too, am very new at Linux.  Though I was very comfortable with DOS command line stuff, I'm still lost in Ubuntu.  I am trying (no, let's make that have already tried) nearly everything to install Rosetta Stone on my single-boot machine.  I can not get Wine or anything else to find the .exe or the .msi files on the CD-Rom.  I simply get a blank browser when I try to find it.  I suppose because it's a windows file, Linux isn't recognizing it.  What can I possibly be doing wrong that it doesn't appear anywhere?  According to the Wine site, Rosetta Stone v.3 is either gold or platinum, depending on where you're reading about it, so I should be able to get it to install.  Butt it beats me how to accomplish that.

---

### Post by starcannon on 2009-07-30
I'm not into genealogy, but I have seen a few posts talking about a linux native program called "Gramps". I don't know if it has the features or abilities that you require, but the price is right, and you can install it from the Synaptic Package Manager.

Menu's
System>Administration>Synaptic Package Manager

Search: gramps

Tick the box to install, click Apply, click Apply again, wait for install to complete, close package manager, find gramps in the menus at Applications>Office>Gramps Genealogy System.

Alternatively, you can install gramps using the command line, open a terminal from menus: 
Applications>Accessories>Terminal
Then copy paste the following:
```

 sudo apt-get install graphviz python-gnome2-extras python-reportlab gramps

```

GL and HF

---

### Post by JoshuaRL on 2009-08-02
> **starcannon said:**
> I'm not into genealogy, but I have seen a few posts talking about a linux native program called "Gramps". 

Rosetta Stone is a language learning application used by top government agencies such as NASA.

[http://www.rosettastone.com/](http://www.rosettastone.com/)

---

### Post by StephenG on 2009-08-03
I was actually entering this fray because I'm having similar troubles with Wine, not with confusing genealogy and language instruction.  When I do a search for "setup.exe" on the computer, I get no responses. In terminal, when I type "cd /cdrom" the command line switches to the CD drive but an "ls" command gets nothing. If I put an audio CD in I get music and I installed Ubuntu on this drive about 2 months ago, so it seems to be working and being recognized by the system. I'm using Wine 1.1.26 and RS 3.4.3A.  The drive absolutely sems to be mounting properly. If I put in the Ubuntu install disc, everything is fine. I can browse to my heart's content. If I put in a disc with Windows files (and I've tried several), however, the drive mounts and the browser opens but there are no files there. Recap: audio files work fine (app opens and they play), Linux files are there and usable, windoze files are unfindable (with or without hidden files option checked). I'm running out of ideas.  (I've got similar posts on another thread on this forum, but am hoping to mine all the info I can find, in case it's missed on the other one.)

---

