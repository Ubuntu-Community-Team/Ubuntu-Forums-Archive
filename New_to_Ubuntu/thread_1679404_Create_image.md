---
title: "Create image"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Rakeshvijayan on 2011-01-31
HI FRIENDS, IS THERE ANY WAY TO CREATE IMAGE FOR MY UBUNTU WORKING SYSTEM .I MEAN LIKE GHOST IN WINDOWS OR PLEASE SUGGEST  ME THE  WAY .. THAT DONT WISH TO LOSS ANY OF MY CONFIGURATION :lolflag:

---

### Post by n213978745 on 2011-02-01
remastersys

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

It allows you to create a live disc image out of your current system with configuration in it.

---

### Post by Hedgehog1 on 2011-02-01
Awesome n213978745!  This is a great find.

I think I will use this very soon myself...

---

### Post by matt_symes on 2011-02-01
Hi

Or clonezilla or dd.

```
man dd
```

You can also back up with tar or rsync.

Kind regards

---

### Post by Rakeshvijayan on 2011-02-04
> **n213978745 said:**
> remastersys

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

it allows you to create a live disc image out of your current system with configuration in it.



is that live cd will be same as my configured ubuntu ,

---

### Post by tea for one on 2011-02-04
> **Rakeshvijayan said:**
> is that live cd will be same as my configured ubuntu ,

Good morning

An Ubuntu image created by Remastersys will contain:-

All your previously installed applications and codecs.
The Ubuntu installation utility to reinstall on another PC (including the partition editor)

Other content depends whether you have included your personal data in the remaster process.

I use Remastersys to keep a copy of my OS in the event of a disaster and I use Grsync (available via the repository) for personal data

Try it because the live remastered CD is your own personal creation and there is a certain amount of self satisfaction when it works.

---

### Post by Rakeshvijayan on 2011-02-07
Thanks for the informations

---

### Post by Rakeshvijayan on 2011-02-07
When I tried to install Remastery on 9.10 ubutnu this was the message 
library@mct:~$ sudo apt-get update

W: Failed to fetch [http://www.remastersys.klikit-linux.com/repository/remastersy](http://www.remastersys.klikit-linux.com/repository/remastersy)
s/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used
 instead.
library@mct:~$ 

first I edit the apt source file add following line 
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/


what happend here .....

---

### Post by ankspo71 on 2011-02-07
Hi,
On the remastersys page for Ubuntu ([http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)), it says to use the following line for Ubuntu 9.10 (Ubuntu Karmic):
> 
For Karmic, Lucid and Newer with grub2 - version 2.0.13-1 and up
```
# Remastersys
deb http://www.geekconnection.org/remastersys/repository karmic/
```


---

### Post by Rakeshvijayan on 2011-02-07
> **ankspo71 said:**
> Hi,
On the remastersys page for Ubuntu ([http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)), it says to use the following line for Ubuntu 9.10 (Ubuntu Karmic):




   I TRIED THAT BUT  STILL THIS IS THE MESSAGE 


W: Failed to fetch [http://www.geekconnection.org/remastersys/repository/Packages.gz](http://www.geekconnection.org/remastersys/repository/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
library@mct:~$

---

### Post by JOHNNYG713 on 2011-02-07
try this, inside the tar is Remastersys all deb

---

### Post by Rakeshvijayan on 2011-02-07
> **johnnyg713 said:**
> try this, inside the tar is remastersys all deb


when i doublick on that tar file this displayed its broken 
):p

---

### Post by Rakeshvijayan on 2011-02-08
OK I INSTALLED IT .MY PROBELM WAS I HAD EDITED THE SORCE FILE LIST /etc/apt/source AND CONTAIN A WRONG ENTRY THERE thanks

---

### Post by Rakeshvijayan on 2011-02-09
> **johnnyg713 said:**
> try this, inside the tar is remastersys all deb



this is the result for me am going to use coustomdist.iso to install is it ok friends

---

### Post by matt_symes on 2011-02-09
Nice :popcorn:

---

### Post by JOHNNYG713 on 2011-02-09
The Dist ISO means **anyone can install it** on there box, It is just like a ubuntu disk you would download and install, Meaning **If you have any delicate items on your dist ISO, ANYONE cold install and see this content ! **. . . Backup ISO is like having your box on a disk! ONLY **you **can access it ! :KS

---

### Post by Rakeshvijayan on 2011-02-10
**thanks [IMG]http://http://img211.imageshack.us/i/errorforremastery.png/[/IMG]**

---

### Post by asmoore82 on 2011-02-10
Clonezilla is exactly what you were looking for: [http://clonezilla.org/](http://clonezilla.org/)

Does remastersys let you restore the backed up system?

---

### Post by JOHNNYG713 on 2011-02-10
> **asmoore82 said:**
> Clonezilla is exactly what you were looking for: [http://clonezilla.org/](http://clonezilla.org/)

Does remastersys let you restore the backed up system?

Yes It makes it makes a full back up that you install as you would any OS ! :guitar:

---

### Post by Rakeshvijayan on 2011-02-17
Dear friends 

I have installed remastey my pc and back up the entire system successfully

 My error was , before i taking back up i changed my logon by (dont ask password for a user )
and i took backup and i Installed it on another pc It log on with out asking password and i change its log on 
ask password when it boot ...here is causing problem it automatically log on again what can i do with this ,):P

---

### Post by Paperloader on 2011-02-17
I use Clonezilla. It works great.

---

### Post by nhtrader on 2011-02-18
> **Rakeshvijayan said:**
> I TRIED THAT BUT  STILL THIS IS THE MESSAGE 


W: Failed to fetch [http://www.geekconnection.org/remastersys/repository/Packages.gz](http://www.geekconnection.org/remastersys/repository/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
library@mct:~$

I just followed the instructions and did the following and it worked fine.

instructions found on ...
     [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

Here's what I did ...

entered terminal mode.

Open file command:
sudo pico /etc/apt/sources.list

Edited file: just add this one line to the bottom of the list of entries already in the file
(I just appended the file with this line...)

deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

exit command: ctrl+X
save command: Y
press Enter  (this prompt appears to confirm filename: File Name to Write: /etc/apt/sources.list )
finished. back to command prompt


Then I used synaptic package manager.
searched for remastersys
found it. selected it for installation.
selected "apply" button

remastersys was installed successfully and it is located in my system menu (i'm using a xfce desktop)

---

### Post by nhtrader on 2011-02-18
Need help with understanding instructions found on  [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Instructions are very clear except for after entry ...
     "In your /home/username directory, make sure hidden files are showing (Control-H is the shortcut)"

For me, using Firefox, the next two images are together and I don't know which files are to be copied.

Does anyone know what files are to be copied?

---

### Post by nhtrader on 2011-02-18
> **Rakeshvijayan said:**
> Dear friends 

I have installed remastey my pc and back up the entire system successfully

 My error was , before i taking back up i changed my logon by (dont ask password for a user )
and i took backup and i Installed it on another pc It log on with out asking password and i change its log on 
ask password when it boot ...here is causing problem it automatically log on again what can i do with this ,):P


I'm glad you got your back up to work. 

 I don't understand what your error was. Would you mind explaining in more detail how usernames/passwords messed you up?

---

### Post by Rakeshvijayan on 2011-02-22
> **nhtrader said:**
> I'm glad you got your back up to work. 
 
I don't understand what your error was. Would you mind explaining in more detail how usernames/passwords messed you up?
 
 
The probelm is ,
1) before taking back up with remastry I changed logon type to "don't ask user name password at loging time'
 
2)when i use _that_ image to install ubuntu 10.04 on another pc that was sucessfull to me ., I changed the logon type to ask user name and password for next restart 
but My new system logon as their parent :confused:

---

### Post by Rakeshvijayan on 2011-02-22
> **nhtrader said:**
> Need help with understanding instructions found on [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
 
Instructions are very clear except for after entry ...
"In your /home/username directory, make sure hidden files are showing (Control-H is the shortcut)"
 
For me, using Firefox, the next two images are together and I don't know which files are to be copied.
 
Does anyone know what files are to be copied?
 
 
 
The tutorial u preffer is better for all and u had point out the confusing sentence I am now confusing there . let me know did you install the remastersys on ur ubutnu .if not please use the tar file on the second page

---

### Post by matt_symes on 2011-02-22
Hi

> For me, using Firefox, the next two images are together and I don't know which files are to be copied.

Does anyone know what files are to be copied?

The files you want to copy are the hidden configuration files for your user. They need to be copied to the /etc/skel directory.

The reason for this is because, when a new user is added to the new install (on the different PC), these configuration folders and settings will be copied to the new users home directory and, therefore, they will have the same settings as you had when you created the remastered Ubuntu distribution.

So copy all the gnome hidden folders and the hidden folders for any applications you have installed. That way a new user will get the same setting as you.

Kind regards

---

### Post by nhtrader on 2011-02-24
Thanks for the replies. 

matt_symes, thanks for clarifying the missing information. Great.

As for * Rakeshvijayan question, "*let me know did you install the remastersys on ur ubutnu", I installed it on Mythbuntu 10.10 which uses xfce 4.6.2, so it basically a modified xubuntu install.

BTW, I did finally get remastersys to work for me and I did not copy the config files to /etc/skel b/c at the time I didn't know that I was supposed to do this.

In the end, I used remastersys to create a customized LiveUSB rather than a LiveCD. Remastersys created the *.iso file I needed and then I used another package "usb-creator-gtk" to transfer this ISO file to the USB stick.

---

