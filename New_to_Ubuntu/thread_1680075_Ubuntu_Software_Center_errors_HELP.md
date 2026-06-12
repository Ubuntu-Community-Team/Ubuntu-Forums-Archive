---
title: "Ubuntu Software Center errors HELP"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by Kaiser13 on 2011-02-01
EDIT: this problem is solved.


I installed the latest version of Ubuntu Notebook 10.10 on my laptop today. in the process of cleaning out programs i came across Python and tried to remove it and got an error about some dll or something. then it prompted me to repair in an endless loop. so i restarted my computer. then ubuntu software center would not show. looking online i tried software-center in the root then sudo apt-get install software-center but now i can click it but it will never show. what is going on? I am pretty knowledgeable about computers but i am new to linix (i installed it on another computer for a couple of months as a test).

EDIT: additional info: i tried to remove python just because it did not seem necessary since i dont program. what i want now is just to get my software center working and be sure whatever i have "installed" is installed and what is "removed" is truely removed. i had to edit menu and remove an icon to a program(byodu something) that was "removed". I have done some reading online but did not discover any solutions.

---

### Post by Ctrl-Alt-F1 on 2011-02-02
According to Wikipedia Software Center is written in Python.  


A lot of Linux programs are written in Python.  It is an interpreted language, so without the python files on your computer the Operating System doesn't know what to do with it.

In a console try:
> 
sudo apt-get install python

P.S. I wouldn't worry too much about software cleanup.  Get used to the Operating System before you start removing components.  As a new user you might be surprised what comes in handy!  If you are going to add or remove software, I definitely recommend doing it exclusively from the software center until you get the hang of it.

The menu editing tool is called alacarte, but it's not super intuitive so please be careful.  You shouldn't need to use it if you use software center to manage your software.

---

### Post by Kaiser13 on 2011-02-02
good to know. i will not remove anything else unless i know otherwise. it still says "starting ubuntu soft..." when i click ubuntu software center in the menu but does not display. thoughts on a solution to that?

---

### Post by Ctrl-Alt-F1 on 2011-02-02
> **Kaiser13 said:**
> good to know. i will not remove anything else unless i know otherwise. it still says "starting ubuntu soft..." when i click ubuntu software center in the menu but does not display. thoughts on a solution to that?

Did you install Python?

---

### Post by Kaiser13 on 2011-02-02
erm. well it wasnt really ever uninstalled. i was not able to remove it. you know the command to install it? sudo apt-get install python ?

---

### Post by Kaiser13 on 2011-02-02
i am almost tempted to format, start anew since it is a relatively fresh install. if i am going to do i better do it before i load my files on it. still i am going to try and troubleshoot for a bit

---

### Post by Ctrl-Alt-F1 on 2011-02-02
Oh.  If it says it's already installed try:

> sudo apt-get install --reinstall python

A fresh install might be a good idea.  If Ubuntu is using the whole disk then you won't need to reformat.  Simply tell it to use the whole disk during install.  If something else (windows for example) is on the same disk then that is a little more complicated.

---

### Post by Kaiser13 on 2011-02-02
josiah@ASUS:~$ sudo apt-get install --reinstall python
[sudo] password for josiah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B/172kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 129748 files and directories currently installed.)
Preparing to replace python 2.6.6-2ubuntu2 (using .../python_2.6.6-2ubuntu2_all.deb) ...
Unpacking replacement python ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up python (2.6.6-2ubuntu2) ...
josiah@ASUS:~$ 


still not fixed. i am going to do the new install. i can do it tomorrow while i watch a movie or something. question: should i use ubuntu 10.10 netbook or is there a more stable version?

---

### Post by Ctrl-Alt-F1 on 2011-02-02
Okay.  Sorry I couldn't be of more help.

On my laptop I run the Desktop Edition (it's for both desktops and laptops).  The netbook edition is supposed to be optimized for small screens, but I don't have any experience with it, as I don't have a netbook.

Ubuntu 10.10 is the latest version.  It should be pretty stable, but if you want what's called long term support then you can download 10.04.  Each version is "supported" for a year and a half, but long term support versions are supported for 3 years.  The next regular (non-long term) release is scheduled for April.  The newer releases are more cutting edge, but they are supported for a shorter amount of time because new ones come out more often.

---

### Post by j0hnnyv on 2011-02-02
Do you actually use a netbook? I have a laptop and run 10.10 desktop and its great. I believe 10.10 netbook comes with unity as default and not gnome....I could be wrong though. I like my gnome :) 10.10 is most stable until 11.04 which will be out in a few months. Then its bye bye gnome ):P, hello unity. :roll:

---

### Post by Ctrl-Alt-F1 on 2011-02-02
> **j0hnnyv said:**
> 10.10 is most stable until 11.04 which will be out in a few months.
This is not necessarily accurate.  The most stable version is whatever works for your hardware.  I've had better luck with LTS versions sometimes, and better luck with the newest release other times.

---

### Post by j0hnnyv on 2011-02-02
Yes I was just going to clarify. TECHNICALLY 10.04 LTS is the most "stable" I have used both and am on a laptop and every single piece of harddrive works for both... even weird things like wireless n usb adapter and wireless printer.

---

### Post by Kaiser13 on 2011-02-02
no its a regular laptop so i'll try desktop. ok i am falling asleep. thank you for your assistance and time. i'll do my research and i won't remove anything i do not completely understand. ty and night

---

