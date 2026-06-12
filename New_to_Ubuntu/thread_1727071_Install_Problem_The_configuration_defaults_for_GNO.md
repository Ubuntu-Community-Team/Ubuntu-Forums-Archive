---
title: "Install Problem The configuration defaults for GNOME Power Management"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by Nachiketkumar on 2011-04-12
I am a new Linux user (Ubuntu 10.10)
yesterday when I installed picassa picture viewer for ubuntu(i386)
after reboot I was not able to log in again 
following error was displayed on right top corner

Install Problem The configuration defaults for GNOME Power Management have not been installed correctly Please contact your Computer Administrator 

Please help me 
](*,)

---

### Post by coffeecat on 2011-04-12
Welcome to the forum.

Googling that error message suggests that one possible cause is that your root partition is full. That may not seem intuitive, but if there is no elbow room so to speak for the system, it's going to put out confused messages. Perhaps installing Picasa filled up whatever spare space you had.

This may not be the problem, but needs excluding. How did you install Ubuntu? Using wubi, that is "inside" Windows, or to its own partition using a bootable live CD or live USB? Do you remember how much space you allocated (or the installer allocated) for Ubuntu?

---

### Post by dcsoldschool53 on 2011-04-12
**Click Applications > Ubuntu Software Center. Type in search "Power Management: without the quotation marks. You may need to re-install it.**

---

### Post by coffeecat on 2011-04-12
> **dcsoldschool53 said:**
> **Click Applications > Ubuntu Software Center. Type in search "Power Management: without the quotation marks. You may need to re-install it.**

The OP is not able to log in to the GUI.

---

### Post by Nachiketkumar on 2011-04-12
I installed Ubuntu inside Windows Vista with 10Gb allocation
and memory may be full but how can I now login I don't need Picassa
but how can I remove it if I cannot log in
:confused:

---

### Post by coffeecat on 2011-04-12
10GB is reasonable, because a default installation of Ubuntu without any added apps, updates and personal data will consume about 2.5GB. But if you have installed a lot and have saved several large personal files, this could be full.

Let's see how full the filesystem really is. Try booting Ubuntu, but when you get the power management error message, press ctrl-alt-F1. You should then see a text-only login. Login - you won't see your password going in when you type it, but it is going in - and then run this command:

```
df -h
```Make a note of the output - it's not that long - and post it here. To reboot, simply:

```
sudo reboot
```

You'll be prompted for your password again and again you won't see it going in.

If that does show a full filesystem then to remove excess files you would need to boot up with an Ubuntu live CD and mount the Wubi virtual disk. You could then browse the Wubi filesystem and delete selected files. If this is necessary I can tell you what you need to do. It would involve downloading a 680-690MB ISO file, burning this to CD, booting up with the CD and then using the terminal. I can give you detailed instructions if you want.

---

### Post by Nachiketkumar on 2011-04-12
I did what you told 
this is what it displayed 




Filesystem   Size  Used Avail  Use% Mounted on
/dev/loop0   11G   9.9G  0     100%    /
none         1.5G  284k  1.5G  1%      /dev
none         1.5G   0    1.5G  0%      /dev/shm  
none         1.5G  304k  1.5G  1%      /var/run
none         1.5G    0   1.5G  0%      /var/lock 
/dev/sda3     70G   65G  4.9G  94%     /host



I will be grateful if you give me any more help

---

### Post by coffeecat on 2011-04-12
Yes, full...

> **Nachiketkumar said:**
> 
Filesystem   Size  Used Avail  Use% Mounted on
/dev/loop0   11G   9.9G  0     100%    /

Almost certainly the cause of your problem.

You have two choices. Either you uninstall Ubuntu wubi from within Windows and then re-install with a bigger virtual drive. A bit drastic and you may need to rescue any personal files.

Or you try the solution I suggested before. If you want to try that and you don't yet have an Ubuntu live CD, go to here:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

And download the ISO for Ubuntu 10.10. Now have a look here for instructions for burning that to CD:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Then you'll need to set your BIOS to boot from CD/DVD, if not already set up this way.

That will keep you busy for a bit and I have to log off for a couple of hours now, but I'll be back and will then post the rest of the instructions.

---

### Post by coffeecat on 2011-04-12
> **coffeecat said:**
> I'll be back and will then post the rest of the instructions.

I'm back with the rest of the instructions.

Assuming you now have an Ubuntu live CD and you have set the BIOS to boot from CD, boot up with the live CD. It's quite slow compared to your wubi install. Choose "try Ubuntu" and you will be taken to the live desktop which should be familiar to you. Now open a terminal (Applications > Accessories) and run these commands:

```
sudo mkdir /win
sudo mount /dev/sda3 /win 
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```Your wubi virtual disc is now mounted to /vdisk and you are ready to delete some superfluous files to make some room. The next command will open a Nautilus file browser window with root privileges. The reason for this is that you are going to delete some root-owned files and also because you will not be able to access your own files without root privileges. (Technical explanation - your UID in your wubi install is different from the UID of the "ubuntu" live account that you are working with.)

```
gksudo nautilus /
```Don't forget the '/' at the end. A nautilus window will open showing you the live session filesystem. Look for the vdisk folder and double-click on it. This will open into the filesystem of your Wubi install - it will look similar to what you saw before.

Now - this next bit is only of use if you have installed applications or updates since installing Wubi. You are going to delete downloaded package files which are cached but of little use. Find the var folder and double-click on it, now cache, apt and then archives. You should now be seeing the contents of /var/cache/apt/archives. You should see a number of *.deb files. Delete them all, but don't delete the partial folder or the lock file. (You can't delete the lock file anyway.)

Now navigate back four levels until you are in your wubi filesystem - **not** the live filesystem. Open the home folder. You will see a folder with your account name. All your personal files are in there. Do you also see a folder called 'tommy'? If you do, that's to do with Picasa but leave it alone for now. Open your account folder and delete as many personal files as you can spare - obviously ones you already have backups of. Choose large size files. We're trying to create room.

Once you've deleted as much as you can, close the root Nautilus window and shut the system down. Now remove the CD and see if you can boot into your wubi Ubuntu. Now and only now think of uninstalling Picasa.

I don't think Picasa was the problem in itself. It was simply the thing that filled your virtual disc up.

---

### Post by Nachiketkumar on 2011-04-14
:D
Thank you Coffeecat
The problem is solved
your solution was perfect 
:P
and I love Ubuntu again and Ubuntu forums too now
and thanks for replying 
dcsoldschool53

---

### Post by coffeecat on 2011-04-14
I'm glad it worked.

Good luck!

---

### Post by Lovek on 2011-04-20
hi, 
I seem to have the same problem. I\m now running a try version of ubuntu from the usb. 
a typed the df -h  command in terminal and got almost exactly the same answer as Nach.. 

I tried the following steps, but it doesn\t work - I guess because I installed it on its own partion (the whole disk - only16gb)

would you know what commands that is suitabel for my case ?

thanks, LoveK

---

### Post by Lovek on 2011-04-20
I now ran  
sudo su  
in terminal

and then the nautilus command
the file system that contains my users home and root and which I before were denied acces to, now changed name from 
15gb filesystem   to a ling comn=bination that didn\t say me anything - allthough still containing the same folders.  but inside my user folder i didn\t find any of my files....

---

### Post by Ymurti on 2011-04-20
Let's see how full the filesystem really is. Try booting Ubuntu, but when you get the power management error message, press ctrl-alt-F1. You should then see a text-only login. Login - you won't see your password going in when you type it, but it is going in - and then run this command:

```
df -h
```Make a note of the output - it's not that long - and post it here. To reboot, simply:

```
sudo reboot
```


Dear coffeecat,

I did it and I got the following result:

Filesystem Size Used Avail Use% Mounted on
/dev/sda5 15G   15G   0    100%   /
none      493M  292k 493   1%     /dev
none      497M   0k  497   0%     /dev/shm
none      497M  188k 497   1%     /var/run
none      497M   0k  497   0%     /var/lock
none      497M   0k  497   0%     /lib/init/rw   

What should I do next?

---

### Post by coffeecat on 2011-04-21
@Lovek, if you installed Ubuntu to its own partition as you say, then you do not have a wubi installation which is what the OP had. Or do you? Are you sure? In either case you would be better starting your own thread describing the error message you get, posting the output of df -h and clarifying whether or not you hvae a wubi install.

@Ymurti, you have copied and pasted from part of one of my posts but without using quote tags, so it looks like yours. Therefore it is not clear whether you are getting the power management error or not. Also, your df -h output does not have a line with "/host" in, which suggests your installation is not a wubi one, therefore different from the OP's. Start your own thread including all the information I've advised Lovek to include.

@Lovek and @Ymurti, it is much better to start your own threads rather than tagging onto ones which may not have the same solution and whose titles may not be relevant. You will get more help with fresh threads.

---

### Post by Lovek on 2011-04-21
ok, yes will do  .. but I , ehm, cant figure out how to start a new thread .... 

anyways i include the info here 

when installing ubuntu I overwrote everything, so no windows on here,  does that make it a non wubi?  
sorry for messing around.

when typing df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  497M   63M  434M  13% /
none                  491M  252K  491M   1% /dev
/dev/sdb1             7.5G  2.7G  4.9G  36% /cdrom
/dev/loop0            652M  652M     0 100% /rofs
none                  497M  168K  497M   1% /dev/shm
tmpfs                 497M  8.0K  497M   1% /tmp
none                  497M   88K  497M   1% /var/run
none                  497M  4.0K  497M   1% /var/lock

---

### Post by coffeecat on 2011-04-21
> **Lovek said:**
> ok, yes will do  .. but I , ehm, cant figure out how to start a new thread .... 

Go to the forum you want to start a new thread in (I would suggest Absolute Beginner's) and click on the "New Thread" button on the  left of the page above the list of threads.

> **Lovek said:**
> 
when typing df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  497M   63M  434M  13% /
none                  491M  252K  491M   1% /dev
/dev/sdb1             7.5G  2.7G  4.9G  36% /cdrom
/dev/loop0            652M  652M     0 100% /rofs
none                  497M  168K  497M   1% /dev/shm
tmpfs                 497M  8.0K  497M   1% /tmp
none                  497M   88K  497M   1% /var/run
none                  497M  4.0K  497M   1% /var/lock

You got that from the live CD/USB, didn't you? That will provide no useful information. For getting the output of df -h, see my post #6, and post the output in your own new thread.

---

### Post by Clyff on 2011-12-18
Hello, I have the same problem but I have looked all over the internet for solutions. It keeps bringing me back to typing terminal commands in recovery mode such as:
 
dhclient eth0
apt-get install -f
apt-get update && apt-get dist-upgrade
 
or
 
sudo dpkg --configure -a
 
or even
 
apt-get purge gnome-power-manager
apt-get install gnome-power-manager
 
But whatever I type in I get the (13) permissions denied error with the question am I root?
 
I haven't ran df -h yet but I'll go do that. I have this on an 80GB HDD with ext4 file system, and 4GB of swap space. It's all formatted and clean.

---

### Post by Clyff on 2011-12-18
df -h
 
/dev/loop0   2.7G | 2.6G | 0 | 100% 
none   1.9G | 280k | 1.9G | 1% /dev
none   2.0G | 0 | 2.0G | 0% /dev/shm
none   2.0G | 80k | 2.0G | 1% /war/run
none   2.0G | 0 | 2.0G | 0% /war/lock
/dev/sda1   14G | 12G | 2.1G | 86% /host

---

### Post by coffeecat on 2011-12-18
@Clyff, welcome to the forum. 

You have a wubi installation, and your problem is that your Ubuntu virtual partition is full.

> **Clyff said:**
> df -h
 
/dev/loop0   2.7G | 2.6G | 0 | 100%

The next problem is that you have reserved only 2.7GB for your Wubi installation. That is not nearly enough. A default installation of Ubuntu takes up about 2.3GB, on top of which you need space for cached files and extra applications even before you store personal files.

The third problem is that your Windows host partition is too small:

> **Clyff said:**
> /dev/sda1   14G | 12G | 2.1G | 86% /host

A 14GB partition is small by Windows standards, and certainly not big enough to accommodate both Windows as host and Ubuntu in a virtual partition. You need to rethink how you are going to install Ubuntu. What you have now is simply not viable - sorry.

Please start your own thread, linking back to this if necessary, and giving details of your hardware and as much as you know about your current partition layout. Then members will be able to help you plan how to install Ubuntu in a way that will work.

---

### Post by CharlesA on 2011-12-18
Back to sleep you go..

---

