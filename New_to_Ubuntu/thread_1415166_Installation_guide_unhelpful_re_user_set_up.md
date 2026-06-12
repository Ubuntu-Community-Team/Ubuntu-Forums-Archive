---
title: "Installation guide unhelpful re user set up"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by ericmarlow on 2010-02-24
I installed Ubuntu 9.10 as the guest OS on VMWare player. The installation is very easy. However, it suggests that you do not use root as your username.
 
Following this recommendation I created a user account and used this to set up my folders etc. I then installed PackETH. When I try to use PackETH to send a packet it says I need SU priviliges. 
 
So I log in as root, go to Users and edit the user privileges by ticking all of the boxes. I then log on as my user again, but PackETH still insists that I need SU privileges.
 
If you cannot use basic software like PackETH without being logged on as root, then what is the point in setting up a different user account? Surely the instructions should be to set up yourself as root in the first place to avoid all this hassle.
 
I also noticed that when logged in as user GNOME terminal would not accept sudo either. It returns Unkown command. I suppose that I have to log on as root even to use GNOME Terminal.
 
I am not impressed. Am I missing something here?
 
Regards,
 
Eric

---

### Post by halitech on 2010-02-24
not sure what changes VMWare player is making but by default, the root user is disabled and you use sudo to gain root priviledges instead of logging in as root.

In order for sudo to work, the user must belisted in the sudoers list.

never used packeth so no idea why it would need root priviledges but sounds like a bad idea to me personally

---

### Post by J V on 2010-02-24
NEVER give root a password
NEVER give yourself su privileges
NEVER... oh wait, ok, you SHOULD use sudo or gksudo to run a program *as* root... :D

---

### Post by ericmarlow on 2010-02-24
> **halitech said:**
> not sure what changes VMWare player is making but by default, the root user is disabled and you use sudo to gain root priviledges instead of logging in as root.

In order for sudo to work, the user must belisted in the sudoers list.

never used packeth so no idea why it would need root priviledges but sounds like a bad idea to me personally
Thank you - I have added my user to the Sudo and root groups. However, PackETH still does not work unless you are logged in as root.
 
In Windows there are a lot of proprietory software packages that will only run if logged on with administrator privileges, so that is normal for me. I only installed Ubuntu so that I could use PackETH, so I will have to use root as my username or it defeats the whole object. It would just have been helpful for the installation instructions to mention this potential problem if you do not use root. It would also be helpful for the repository to identify packages requiring you to be logged on as root to work.
 
Regards,
 
Eric

---

### Post by ericmarlow on 2010-02-24
> **J V said:**
> NEVER give root a password
NEVER give yourself su privileges
NEVER... oh wait, ok, you SHOULD use sudo or gksudo to run a program *as* root... :D
 
 
That's all very well. but its the only way I can run PackETH, and that was the only reason I installed Ubuntu in the first place. I did try right click to find a "run as" option but no such luck. How would I use sudo when clicking Applications\Internet\PackETH with my mouse button then?
 
Regards,
 
Eric

---

### Post by halitech on 2010-02-24
instead of logging in as root, why not locate the packeth file and create a custom launcher to run it with sudo?

in a terminal run
locate packeth

then create the launcher with gksudo packeth ?

its probably located in /usr/bin

---

### Post by ericmarlow on 2010-02-25
> **halitech said:**
> instead of logging in as root, why not locate the packeth file and create a custom launcher to run it with sudo?
 
in a terminal run
locate packeth
 
then create the launcher with gksudo packeth ?
 
its probably located in /usr/bin
 
 
**GOLD STAR** to Mr Halitech ( no relation to Halitosis I hope! ) - the suggested commands do launch PackETH as root. However 2 problems:
 
1 Each time I wish to start PackETH I have to open the Terminal and type the commands - it does not appear to "create a launcher" but merely launches the application. Still that's a start.
 
2 The file system then appears to be that of root, and the files to load and save are in the "root" directory. 
 
To be honest I cannot see any advantage over running with root as my user name in the first place. I am used to running with Domain Administrator privileges in Windows and I know the risks. Nevertheless for IT beginners the suggested solution is a good one.
 
Thank you Mr Halitech. 
 
Regards,
 
Eric

---

### Post by halitech on 2010-02-25
the command gksudo packeth doesn't actually create a launcher, it simply runs the command. If you right click on the desktop, you should get an option to create launcher, that is where you would type gksudo packeth so you would have a "shortcut" on your desktop. You can also press ALT + F2 and type the command in instead of opening the terminal to run the command.

yes it will be the root file system because you are running the command with root priviledges.

The reason for doing this instead of running as root is to protect the rest of the system from being open to attack from the internet and malicious code. If you decide to run as root, be aware that you are responsible for any bad things that will happen to your system.

Good luck.

---

### Post by ericmarlow on 2010-02-26
> **halitech said:**
> the command gksudo packeth doesn't actually create a launcher, it simply runs the command. If you right click on the desktop, you should get an option to create launcher, that is where you would type gksudo packeth so you would have a "shortcut" on your desktop. You can also press ALT + F2 and type the command in instead of opening the terminal to run the command.
 
yes it will be the root file system because you are running the command with root priviledges.
 
The reason for doing this instead of running as root is to protect the rest of the system from being open to attack from the internet and malicious code. If you decide to run as root, be aware that you are responsible for any bad things that will happen to your system.
 
Good luck.
 
Many thanks Halitech - the launcher cracks it, although its still confusing having to use 2 user file systems. Almost as bad as Windows "My documents" which can be different for the SAME user name, but run as as local, domain1 and domain2 - as I found out many years ago. No doubt one day I will actually be able to navigate between the different users files.  For now though I'll have to put all the saved files for root applications into the root directory. At least that way I can find them again.

---

### Post by Zill on 2010-02-26
ericmarlow:  I am pleased that you have resolved your problem.

You may find the link below useful in explaining "the Ubuntu way" regarding root.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

