---
title: "Avg"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by xfatherjack@yahoo.com on 2008-12-08
AVG_v7 for Linux & and  dazuko.
I DO NOT understand much about Computer, their language OR systems.
I am used to Computers that run MS Windows where everything install AUTOMATICALLY.
I am completely NEW to Linux.	
I have installed “ ubuntu 8.04 “ on my system (8.1 was  all bugs).
I downloaded a list of linux commands and installed a package Ultamatics 
My Goal was to Install AVG-Free security in my computer.
I downloaded “ avg75lms-r52-a1367.i386.deb “ 
and “avg75lms-r52-a1367.i386.tar.gz”, I also got an email with my Licence 'Key' number.
I used 'Gdebi Package Installer' to install “ avg75lms-r52-a1367.i386.deb “ 
I was not asked for my Licnce Number, Idid not get a Launch Icon.
I was not asked to Regester or To Accept the (standard) Agreement.
I tried to install “avg75lms-r52-a1367.i386.tar.gz”. 
I could not get it installed
Reading some Tech-Geek STUFF it looks like I have to have something called
“  dazuko  “ running/available on my sysyem to install AVG.
So I downloaded “  dazuko-2.3.5.tar.gz  “ to my Desktop
Dazuko Install attempts......
I next ran the command “  cd /home/donal/Desktop/  “.
I ran “ ls “ to check my Dektop files. 
I now have “ dazuko-2.3.5.tar.gz “
to uncompress the archive..using the 'tar' command.......
I ran     “ tar xvfz dazuko-2.3.5.tar.gz “
I ran “ ls “ again to check my NEW Dektop files......
Now i have “ dazuko-2.3.5.tar.gz “ and “  dazuko-2.3.5  “
Next...  go to the directory that contains all the extracted 'Files'
...using the 'cd' command.....
I ran “ cd dazuko-2.3.5 “  and .....
then I ran “ ls “ again to check my NEW Dektop files.......
NO Install/Application File
WHAT do I do NOW to install ???? 

I need “The FOOLS Guide“.
A Line-by-line set of instructions.
Please No “Geek” Stuff,
I understand English but not 'Teck' or 'Computer-talk'.
Please Help a Hopefull NOVICE*!!!!
Jack

---

### Post by clive littlewood on 2008-12-08
Hi

Short answer is you don,t need it in Linux unless you are transfering files to windows.

All you you need to do with a .deb file is double click on it and it will self install.

Try to simplify your questions and post each question in it,s own thread.

Hope this helps   :p


Clive

---

### Post by opscure on 2008-12-08
The tar.gz file was likely the program's source code.

While you are in the dazuko-2.3.5 directory type:
```
./configure
```
```
make 
```
```
sudo make install
```


This should build your source files into something binary.  I don't know why you are doing it this way though.  Building files from source is definitely geekier then binary packages, like your .deb file.

You should probably follow the installation instructions for ubuntu on this page:

[http://www.debianadmin.com/protect-ubuntu-desktop-from-viruses-using-avg-antivirus.html]("http://www.debianadmin.com/protect-ubuntu-desktop-from-viruses-using-avg-antivirus.html")

---

### Post by leveliv on 2008-12-08
8.10 now is pretty rock solid stable.

Anywho...the one thing I liked about using ubuntu was the security factor that I didn't need the firewalls or virus scanners cause there was no need, but What you have there is a automated installer much like a .exe (in my opinion anyways) Only a select few programs I have seen have the EULA agreement, which I can't say that I miss, I usually mindlessly click through those anyway.

and the other is a source by the looks of things. 
Here is the guide that I have used...since I was with 5.04 
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)

---

### Post by carml on 2008-12-08
Are you sure you need to install dazuko to use AVG:confused:?
I installed Avast (for scruple),and I call it via shell...

---

### Post by CompShrink on 2008-12-08
You do need dazuko for on-demand scanning (ie scanning each new files when it is downloaded), but not if you just want to scan the whole computer.

By the way, anything I put in code boxes should be done on a terminal. Anything you read with a # or $ in front usually should be run in a terminal. Sometimes you will have to run it with ```
sudo
``` before the command, to give it "root privileges" which is the same as "administrator rights" in Windows.

The AVG icon should show up in Applications in the top left of your screen. If not, open a terminal and run: ```
avggui
```

The manual for AVG linux is here: [http://free.avg.com/download?prd=afl#tba2](http://free.avg.com/download?prd=afl#tba2) 
Look at section 3.3 for the license key answer, and section 3.5 for running AVG. And probably other sections if you need to.

To install dazuko, follow the instructions in part 2.1 here:

[http://www.dazuko.org/tgen.shtml](http://www.dazuko.org/tgen.shtml)

You do NOT need parts 2.2 and below.

Note that the last line, ```
modprobe dazuko
``` is not permanent, it loads dazuko but next time you restart your computer it will not be loaded. To make it load every time you turn on your computer, do the following.

```
gksudo "gedit /etc/modules"
```
with " included, and then add > dazuko at the end, on it's own line with nothing else on that line.

---

### Post by gandaran on 2008-12-08
[email]xfatherjack@yahoo.com[/email]
you can install any anti-virus, but remember they only scan for windows virus, they are practically useless for protecting your ubuntu/linux system, but you can use them to scan downloaded files for virus before passing them to windows computers   
avg is good and complete, you don't need it, you can get a .deb package from avg website, don't install the tarball package, you'll regret it if you decide to remove avg, install only the .deb package and don't install dazuko, you'll have a big problem geting it to work (it conflicts with apparmor).
I would rather recommend a more simple and good free antivirus install like bitdefender [http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Beta/EN/Linux/deb/](http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Beta/EN/Linux/deb/) the 1.0.1 packages include a graphical gui you can find in applications » system tools

---

