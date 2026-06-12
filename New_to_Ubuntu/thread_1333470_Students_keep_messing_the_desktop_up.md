---
title: "Students keep messing the desktop up"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by madfrenzy on 2009-11-21
Hi all,
I've been using ubuntu for about 2 years now (luckly I got windows out of my system :) ) and I'm an instructor and I turned all the PC's in the labs to ubuntu, but students keep changing the panels and deleting the notification area and stuff like that, so I wanted to do something to overcome this problem, and that summarizes my question into :

How to tell the OS to give the user a new home folder after each reboot but at the same time keep the initial shortcuts ( that I put manually after setup ) on the desktop (I dont care about what the students put on the desktop after that).

Hopefully someone would help me.

Thanks in advance
Mina Makary

Edit : I have found this, but I dont understand it.

1. limit the directories the users have access to (probably just to /home/username)
2. Get the desktop and other stuff looking how you want it.
3. Make a tarball of the /home/username directory tar -cvjpf /home/username filename.tar.bz2
4. add some lines to your desired logoff script to delete the contents of the directory and extract the tarball to it
rm -Rfv /home/username/*
tar -xvjpf filename.tar.bz2 -C /home/username

---

### Post by twisted_steel on 2009-11-21
Check out these two guides:

[http://library.gnome.org/admin/deployment-guide/](http://library.gnome.org/admin/deployment-guide/)

[http://tombuntu.com/index.php/2008/05/27/how-to-lock-down-gnome/](http://tombuntu.com/index.php/2008/05/27/how-to-lock-down-gnome/)

They should at least help with your panel problems.

---

### Post by madfrenzy on 2009-11-21
Thanks alot I'll check them out

---

### Post by praveesh on 2009-11-21
> **madfrenzy said:**
> Hi all,
I've been using ubuntu for about 2 years now (luckly I got windows out of my system :) ) and I'm an instructor and I turned all the PC's in the labs to ubuntu, but students keep changing the panels and deleting the notification area and stuff like that, so I wanted to do something to overcome this problem, and that summarizes my question into :

How to tell the OS to give the user a new home folder after each reboot but at the same time keep the initial shortcuts ( that I put manually after setup ) on the desktop (I dont care about what the students put on the desktop after that).

Hopefully someone would help me.

Thanks in advance
Mina Makary

Create a script to be executed at startup . The script should first delete everything in home folder . Then it should copy the icons you wish to place in the desktop (you have to first keep the icons or shortcuts to be copied in a seperate folder outside home folder).

To create script, open a text editor and type (I assume that the address of the folder in which you placed the icons to be copied is ADDRESS): 

#! /bin/bash
cd ~ 
rm -r *
cd ADDRESS
cp -r * ~/Desktop


then save this file in a file name you wish . I suppose the name you have given is 'NAME' . Copy this file to /bin   folder(for that you may want to type gksu nautilus  in terminal) . Change permission of file to be readable by the user . 

Them go to system->preferences->startup_applications  . Click on add . At the box to type command , type NAME . Give a name and Save . 

Done 
was that helpful ? Do you want further explanation ?

---

### Post by efflandt on 2009-11-21
It is rather dangerous to tell a anyone to put [COLOR=Red]**rm -r ***[/COLOR] in a script that runs from an undetermined location, since that would recursively remove all files and directories that user has permission to remove under the current working directory, which is not necessarily the dir the script is in.  So imagine what would happen if the script was run as root while current working dir was /etc or /, or a user tested it before everything to restore it was in place and correct.  Such a statement should either cd to a specific dir first, or have a more specific path prefix on wildcard *****

Hopefully nobody will try that as the only user who can log into a system, or after they have done "sudo su".

---

### Post by madfrenzy on 2009-11-21
Thanks for the fast reply, so what I will do is change "ADDRESS" by the address of the folder that I'll copy the contents of the home folder in ?? and I have another question, what will (rm -r *) will do??

Thank you very much for your help

---

### Post by nikhilbhardwaj on 2009-11-21
there's an xguest package
in fedora and mandriva
it allows the user to log in and use the system
but upon logging out all the changes are forgotten

you could see if it is available for ubuntu too

---

### Post by Shpongle on 2009-11-21
> **madfrenzy said:**
>  what will (rm -r *) will do??


it will recursively remove all files and directories that user has permission to remove under the current working directory. 

if using rm its better to use it with rm -vi which will tell you what its deleting and asks if your sure

---

### Post by NoaHall on 2009-11-21
> **DillByrne said:**
> it will recursively remove all files and directories that user has permission to remove under the current working directory. 

if using rm its better to use it with rm -vi which will tell you what its deleting and asks if your sure

Not if you want a automatic script.

Instead, you should use
rm -r /home/USER/*

---

### Post by renkinjutsu on 2009-11-21
i say mount all of the computer's /home folder to the same directory on a server on READ-ONLY mode..

that way, the changes they make, wouldn't be written to disk, and if you wanted to change something, you can just change it on the server, and it'll change for EVERY computer..

---

### Post by praveesh on 2009-11-21
> **efflandt said:**
> It is rather dangerous to tell a anyone to put [COLOR=Red]**rm -r ***[/COLOR] in a script that runs from an undetermined location, since that would recursively remove all files and directories that user has permission to remove under the current working directory, which is not necessarily the dir the script is in.  So imagine what would happen if the script was run as root while current working dir was /etc or /, or a user tested it before everything to restore it was in place and correct.  Such a statement should either cd to a specific dir first, or have a more specific path prefix on wildcard *****

Hopefully nobody will try that as the only user who can log into a system, or after they have done "sudo su".

I agree . Changed the post . The default directory will be home directory that's why I told so

---

### Post by praveesh on 2009-11-21
> **madfrenzy said:**
> Thanks for the fast reply, so what I will do is change "ADDRESS" by the address of the folder that I'll copy the contents of the home folder in ?? and I have another question, what will (rm -r *) will do??

Thank you very much for your help

rm is the command for deleting . -r is the option  for deleting folders too . * for everything  in the working folder. (I MADE A CORRECTION TO THE SCRIPT PLEASE NOTE THAT. ). That is delete everything in the current directory(folder). By default, the working folder will be your home folder . So it will delete everything inside the home folder . To ensure the working directory is home folder , add cd ~  before the rm -r * 
    
cp is the command to copy ;it will copy every thing in the current working directory to the directory whose address is followed by the cp . Eg : cp * ~/Desktop  will copy everything in the current working folder(or working directory)  to desktop. You can see a folder Desktop inside your home folder  


Note : ~ means address of home folder . * means everything


cd is the command to change working folder(cd followed by the address of the new working folder).


I hopes that helped you . Further explanation ?

---

