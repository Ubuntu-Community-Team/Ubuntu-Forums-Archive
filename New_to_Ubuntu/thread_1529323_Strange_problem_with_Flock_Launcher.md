---
title: "Strange problem with Flock Launcher"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Orange_Ribbon on 2010-07-12
Okay,  for some reason Firfox was crashing my system so I wanted to try new browsers.  Well my only requirment is spell checker so I decided to try flock.  So far I like it but to launch it I have to open Nautalis with the sudo command in terminal and then double click on my launcher.  

Here is my launcher

[Desktop Entry]
Version=2.5
Encoding=UTF-8
Name=Flock
Comment=Flock Web Browser
Exec="/home/jason/flock/flock-browser"
GenericName=Flock Web Browser
Icon=/home/jason/flock/icons/mozicon128.png
Path=/home/jason/flock
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-KDE-SubstituteUID=false
X-KDE-Username=
Categories=Network;Application;
GenericName[en_US]=Flock Web Browser

All the permissions are set to jason for this file and all the files in the flock folder.    

What am I doing wrong?

---

### Post by gandaran on 2010-07-12
what type of package did you instal?
you could get a flock .deb package from [getdeb]("http://www.getdeb.net/updates/ubuntu/10.04/") install and you would have a launcher in applications » internet » Flock.
if you downloaded the tar package and extracted it where did you put it? in home user folder? you don't need to be root to launch flock!
just make a simple launcher, right click desktop area, choose to make launcher, type Flock in name field and the path to flock-browser file in command field, you now have a desktop launcher!, I find it hard to believe how simple things turn out complicated for some users! 
or did you change (unnecessary) permissions to the flock file or folder?

---

### Post by Orange_Ribbon on 2010-07-12
The getdeb site kept on hanging up on me in konkquor and epiphany.  I was fallowing the instructions on their website since I am relatively new to Linux.  (at best I am an off and on user)  

I extracted the tar to my home folder 

/home/jason/flock

the folder and files inside have permissions for me to use them.

same with the launcher

also when I tried just creating a launcher on the panel and linking it to the same file the launcher was linking to and still nothing.

---

### Post by gandaran on 2010-07-12
> the folder and files inside have permissions for me to use them
where did you get this idea you need permissions to run flock, you don't need any permission thing running flock from your home directory or even if you install flock in root file system you can still run it as user.
I suggest you try deleting everything relating to flock, this includes the visible flock folder and the flock user profile (home/user/.flock, the hidden home part) and your launcher too then download the tar package again, extract it by right clicking the tar package and choose extract here, then make the launcher again, don't forget the launch command is the full path to the flock-browser file.
post back if still no work.

---

### Post by Orange_Ribbon on 2010-07-15
Tried that, it still didn't work.  Now when my launcher that I got from their website didn't work I just created one and linked it to the same file,  and that didn't work.  So I changed it to a terminal app and put sudo in front of the path, and that worked after I put my password into the the terminal window that popped up :-(

I extracted it the same way you told me by just using the menu and saying extract here.

---

