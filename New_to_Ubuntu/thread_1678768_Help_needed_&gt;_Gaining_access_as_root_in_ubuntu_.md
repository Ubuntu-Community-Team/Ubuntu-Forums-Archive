---
title: "Help needed &gt; Gaining access as root in ubuntu 10.10"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by mind_over_matter on 2011-01-30
Hello everyone... Im a total newbie to Ubuntu/linux 3days lol, Im loving the os from converting from a heavy windows users the performance is amazing and really like the interface and glad to have made the move... however at the moment Im still dual booting with vista which is fine but I want to learn as much as possible in linux...

Here is my problem... when trying to install VMplayer and other apps it comes up with the error --> root access is required for the operations you have chosen.

How do I get root access to install software Ive looked over the net and there is so many mixed answers and some scary lol saying to be  root is dangerous etc... please please help me understand how I can can be root user to install software !!! driving me crazy and preventing me from enjoying the great os 

To be clear Im using super_os_ubuntu 10.10
There is only 1 user on the machine me who is set to admin user already ? Any and all help would be greatly appreciated...

Finally any suggestions on where to find/search/learn the basics with terminal and command lines ?

---

### Post by pi3.1415926535... on 2011-01-30
To use root in terminal type sudo in front of the command. Though be careful, as sudo has a greater ability to delete important files. In order to install through terminal use "sudo apt-get install *package-name*". Also to learn about a terminal command, man *command*.

---

### Post by bapoumba on 2011-01-31
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) :)

---

### Post by sffvba[e0rt on 2011-01-31
In **sudo** we trust!


404

---

### Post by Rubi1200 on 2011-01-31
To be honest. of this is all new to you then start first installing from the Ubuntu Software Center.

When it asks for authentication, type in the password you set when installing.

---

### Post by Ctrl-Alt-F1 on 2011-01-31
Gaining root access CAN be dangerous.  It is essentially the same thing as being an administrator in Windows, except that you can basically delete ANYTHING.

Using sudo is more akin to using user access control in Windows (the little box that pops up and asks you if you want to give a program permission to run), as it allows you to run commands and programs with root privileges for a shorter amount of time.

To run a command with root privileges just put sudo in front of it.  If you are trying to run a graphical app with root privileges use gksudo.

As someone else said you can usually get all the apps you need from the software center more easily.

---

### Post by mind_over_matter on 2011-01-31
Thanks for the replies, I tried the sudo command and got this:confused:
dan@ubuntu:~$ sudo apt-get install VMware-Player-3.1.1-282343.i386.bundle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package VMware-Player-3.1.1-282343.i386.bundle
E: Couldn't find any package by regex 'VMware-Player-3.1.1-282343.i386.bundle'
dan@ubuntu:~$ 

Ill have to read through the link posted by admin an take my time to get to terms with things im sure its worth the patience.

I have already used the ubuntu software centre to install and all was ok but the selection is limited unless I havent searched that to its full extent yet..

---

### Post by Ctrl-Alt-F1 on 2011-01-31
> **mind_over_matter said:**
> Thanks for the replies, I tried the sudo command and got this:confused:
dan@ubuntu:~$ sudo apt-get install VMware-Player-3.1.1-282343.i386.bundle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package VMware-Player-3.1.1-282343.i386.bundle
E: Couldn't find any package by regex 'VMware-Player-3.1.1-282343.i386.bundle'
dan@ubuntu:~$ 

Ill have to read through the link posted by admin an take my time to get to terms with things im sure its worth the patience.

I have already used the ubuntu software centre to install and all was ok but the selection is limited unless I havent searched that to its full extent yet..Don't use apt-get install if you downloaded it from the web.  Just cd to the directory that it is contained in (i.e. cd /home/usr/Jon/Documents) then type 

> sudo ./NAME-OF-VMWARE-BUNDLE-GOES-HERE

If you start typing the name of a file and hit tab it will automatically fill in the name of the file.

---

### Post by magestickown on 2011-02-24
> **mind_over_matter said:**
> Hello everyone... Im a total newbie to Ubuntu/linux 3days lol, Im loving the os from converting from a heavy windows users the performance is amazing and really like the interface and glad to have made the move... however at the moment Im still dual booting with vista which is fine but I want to learn as much as possible in linux...

Here is my problem... when trying to install VMplayer and other apps it comes up with the error --> root access is required for the operations you have chosen.

How do I get root access to install software Ive looked over the net and there is so many mixed answers and some scary lol saying to be  root is dangerous etc... please please help me understand how I can can be root user to install software !!! driving me crazy and preventing me from enjoying the great os 

To be clear Im using super_os_ubuntu 10.10
There is only 1 user on the machine me who is set to admin user already ? Any and all help would be greatly appreciated...

Finally any suggestions on where to find/search/learn the basics with terminal and command lines ?

I got access to root (login) by typing 
sudo passwd root
then logging out, and going to login with other user, typing 'root' and the password you selected.
you can lock it again by typing
sudo passwd -l root

---

### Post by 3rdalbum on 2011-02-24
> **magestickown said:**
> I got access to root (login) by typing ...
you can lock it again by typing
sudo passwd -l root

Please don't advised users to do this. It just encourages new users to run as root full-time, which is not a good idea. Sudo is plenty good enough for the OP.

---

