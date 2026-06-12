---
title: "Urgent Help Needed :("
date: 2009-01-22
forum: New to Ubuntu
---

### Post by feras.ws on 2009-01-22
Dear Members :

:( From the damn windows I say hello !
I was playing with the chmod command , when I changed the etc permissions !! now I cannot log in to my system !
& when I entered the recovery mode & used the command line , I wrote chmode -R 777 /
but nothing happens , a message appears saying : changing permissions for : "directory" , read only directory !
what should I do ?
I cannot log in to my system :(

Regards
Feras

---

### Post by mcduck on 2009-01-22
I'd say the easiest way is to do a fresh install.

You *really* should not change permissions of system directories. There's no simple way to return the correct permissions as different files & directories need to be owned by different users and groups and need different permissions to work correctly.

Use a live-CD to backup your home directory (if you haven't got a separate home partition) and make a fresh install.

---

### Post by feras.ws on 2009-01-22
:( I have two separated drivers for Ubuntu ! and unfortunately the CD'S i passed them to my friends :) 
I really need a help!
I have 8.04 Kubuntu &maybe Ubuntu .

regards
feras

---

### Post by jpoRS on 2009-01-22
If you have 8.04 you can install that and either run that for the remainder of its lifespan (April 2011), or just upgrade right into 8.10

Hope this helps,
jim

---

### Post by feras.ws on 2009-01-22
I don't know ! all the solutions says that I have to re install :(

---

### Post by mcduck on 2009-01-22
> **feras.ws said:**
> I don't know ! all the solutions says that I have to re install :(
If you want, I can give you a list of correct permissions & ownerships for each file. That's about 4000 files (on my system). Then you'd have to go through each file and set the correct permissions & ownership by hand. Like I said, re-install is the easiest way.

---

### Post by feras.ws on 2009-01-22
> **mcduck said:**
> If you want, I can give you a list of correct permissions & ownerships for each file. That's about 4000 files (on my system). Then you'd have to go through each file and set the correct permissions & ownership by hand. Like I said, re-install is the easiest way.
hmmm , Ok i'm convinced in reinstalling but as a question  ,can I take a backup for all the files I have & all the programs I installed?
and if re installed the 8.04 Ubuntu , do you know how many Mega bytes the update takes?

Regards
Feras

---

### Post by beren.olvar on 2009-01-22
Hi, 
before you try reinstalling, try to change the permissions from the live cd.
Through nautilus should be quite easy, or just

sudo chmod -R 755 /etc

I think you will lose some functionalities, but nothing you cant change later...
If doesnt work with 755, try 777 and after you have your machine working set lower permissions for the important files... you could upload a list with the files you are interested in and I (or anyone) could give you the permissions they have on my (their) system.

Edit: many files in the /etc passwd are escential, but many others are just default configs and stuff that doesnt need to have a specific permission. If your computer is used as a desktop computer, used only by trusted people, then I dont think you should worry too much about that.

Hope you have good luck!!
cheers!

---

### Post by Nevyn on 2009-01-22
A small tip before you reinstall: use a separate partition for your /home. You set this during the installation process, when it's asking where on the disk you want to put your ubuntu. 
With a separate /home you can reinstall 20 times per day and never need to backup or restore your settings or files (even though backup always is important). I reinstalled my ubuntu 5 times or something yesterday after messing with a new graphics card. It only takes about 20 minutes to do a full reinstall.

If you need any help dong this, just post here :)

Good luck!

---

### Post by mcduck on 2009-01-22
> **feras.ws said:**
> hmmm , Ok i'm convinced in reinstalling but as a question  ,can I take a backup for all the files I have & all the programs I installed?
and if re installed the 8.04 Ubuntu , do you know how many Mega bytes the update takes?

Regards
Feras

If you backup your home directory (including all the hidden files) all settings for all your programs & desktop will be saved.

Backing up installed programs is not possible, but if you haven't ever cleared package manager's cache you'll find all the packages you have installed & all updates in /var/cache/apt/archives. You can backup them as well, and after the re-install run "sudo dpkg -i *.deb" in the directory where you put the packages to re-install all of them at once. That should save quite a bit of time as you wouldn't need to download them again.

If you re-install with 8.04 and upgrade to 8.10 you'll end up using about the same amount of disk space as fresh install of 8.10. Although you will need a bit of extra disk space during the upgrade itself. If you are concerned about downloading the updates, that would be about the same as downloading the latest install disk.

---

### Post by hyper_ch on 2009-01-22
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Paqman on 2009-01-22
> **feras.ws said:**
> I entered the recovery mode & used the command line , I wrote chmode -R 777 /


I agree that a reinstall is probably the quickest solution. However, i'm also concerned that you ran this command. 

[LIST]
[*]Do you understand why it would be a bad idea to run this from recovery mode? It would be equally bad in normal mode if you'd used sudo, btw.
[*]What did you expect it to do?
[*]Do you understand why your system has become unusable because of it?
[/LIST]

---

### Post by feras.ws on 2009-01-22
> **Paqman said:**
> I agree that a reinstall is probably the quickest solution. However, i'm also concerned that you ran this command. 

[LIST]
[*]Do you understand why it would be a bad idea to run this from recovery mode? It would be equally bad in normal mode if you'd used sudo, btw.
[*]What did you expect it to do?
[*]Do you understand why your system has become unusable because of it?
[/LIST]
hmmm , I think using sudo is disabled because it gives any one the ability to mess with my computer :) without any effort !!

I don't know what should I do know !
re installing is recommended but unfortunately i have only Kubuntu 8.04 , & open suse 11 :(

Regards
Feras

---

### Post by feras.ws on 2009-01-22
can I ask a question ?
is there any way that i can change the permissions for those folders under Windows ?

Regards
Feras

---

### Post by KIAaze on 2009-01-22
> **feras.ws said:**
> 
I was playing with the chmod command , when I changed the etc permissions !!


**NEVER "PLAY" WITH COMMANDS AS ROOT.**
chmod can be learned by playing around in your home as a normal user.
If you are learning how to use commands, it's always better to play around in a temporary directory with temporary files.
"Playing" as root is only necessary if a command requires root permissions.
And in that case, it's always best to read some documentation first or follow a tutorial!

As for reinstalling your programs: [http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

Program settings are stored in your home directory, so if you back that up, you shouldn't have any problems.

> **feras.ws said:**
> can I ask a question ?
is there any way that i can change the permissions for those folders under Windows ?

Regards
Feras
I believe not (but am not sure).
But you can access them:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

> **feras.ws said:**
> hmmm , I think using sudo is disabled because it gives any one the ability to mess with my computer :) without any effort !!

I don't know what should I do know !
re installing is recommended but unfortunately i have only Kubuntu 8.04 , & open suse 11 :(

Regards
Feras

You can install 8.04 and upgrade.
To get Gnome instead of KDE:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by feras.ws on 2009-01-22
> **KIAaze said:**
> **NEVER "PLAY" WITH COMMANDS AS ROOT.**
chmod can be learned by playing around in your home as a normal user.
If you are learning how to use commands, it's always better to play around in a temporary directory with temporary files.
"Playing" as root is only necessary if a command requires root permissions.
And in that case, it's always best to read some documentation first or follow a tutorial!

As for reinstalling your programs: [http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

Program settings are stored in your home directory, so if you back that up, you shouldn't have any problems.
well thank you very much , I was installing  a compiler ! & unfortunately it has a folder called etc ! they asked me to change it's permissions but I was as root :) so everything changed !
I found Ubuntu 7.10 cd , can I change permissions throw it or no ?

Regards
Feasr

---

### Post by KIAaze on 2009-01-22
Yes, I think you should be able to change permissions with it.

What compiler were you installing?
Asking to change the permissions for /etc seems kind of strange...:confused:

---

### Post by KIAaze on 2009-01-22
> chmod -R 777 /
[SIZE="5"]**THIS IS MADNESS!**[/SIZE]

Sorry, I just had to. ^^

---

### Post by feras.ws on 2009-01-22
> **KIAaze said:**
> Yes, I think you should be able to change permissions with it.

What compiler were you installing?
Asking to change the permissions for /etc seems kind of strange...:confused:

:) X# compiler :)
it was asking to change the etc in the compiler's folder not the main one :D but I miss understood !

Regards
Feras

---

### Post by feras.ws on 2009-01-22
I tried both programms but they are useless ! :(

---

### Post by feras.ws on 2009-01-23
I downloaded 8.10 and burnt it ! and installed Ubuntu again , My question now , how can I re install Ubuntu ? I mean overwrite the old version ?
and is reinstalling will delete all my data ?

Regards
Feras :(

---

### Post by beren.olvar on 2009-01-23
I dont get you. Whats your new configuration?? where you installed ubuntu again? different partition, same partition? 
could you post the output of 

sudo fdisk -l /dev/sda
(and any other hdd you have)

Anyway, before proceding (what ever your nextstep is) you should backup any important data you have.

cheers

---

### Post by KIAaze on 2009-01-23
> **feras.ws said:**
> installed Ubuntu again , My question now , how can I re install Ubuntu ?

So you reinstalled it already and are asking how to reinstall it? O.o

Overwriting the old version is easy. All you have to do is install to the same partition.

[LIST]
[*]If your home directory is on the same partition as your root directory, then yes, **it will delete all your data!**
[*]If your home directory is on a separate partition, then Ubuntu 8.10 should detect it and ask you if you want to reuse it. This way, your data is safe. :) (but if you can back up, back up first, just to be safe.)
[/LIST]

Home auto-detection info:
[http://brainstorm.ubuntu.com/idea/138/](http://brainstorm.ubuntu.com/idea/138/)
[https://wiki.ubuntu.com/RecommendSeparateHome](https://wiki.ubuntu.com/RecommendSeparateHome) (only screenshots I could find)

_If you need partitioning help:_
I'm not sure I understood your current status clearly.
Do you have terminal access? GUI access?

_If you have terminal access:_
Post the output of the following two commands:
```
sudo fdisk -l
df -h
```

"fdisk -l" will list all your partitions (sounds like "format disk" and can probably be used for that too, but with '-l', it just lists partitions. ;))
"df -h" gives an overview of where what is mounted.

_If you have GUI access:_
Run gparted and post a screenshot. :)

---

### Post by feras.ws on 2009-01-23
> **beren.olvar said:**
> I dont get you. Whats your new configuration?? where you installed ubuntu again? different partition, same partition? 
could you post the output of 

sudo fdisk -l /dev/sda
(and any other hdd you have)

Anyway, before proceding (what ever your nextstep is) you should backup any important data you have.

cheers

well I had Ubuntu version installed & i was using it , but yesterday i was playing with the chmod command so I lost everything ! and i cannot log into my system any more , so I installed Ubuntu again on a different partition ! I'm trying to change the old permissions to log into my old system !
here is the output
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79a9e71f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         192       10941    86341632    7  HPFS/NTFS
/dev/sda3           10941       15665    37945530    7  HPFS/NTFS
/dev/sda4           15666       19457    30459240    5  Extended
/dev/sda5           15666       16029     2923798+  82  Linux swap / Solaris
/dev/sda6           16030       17245     9767488+  83  Linux
/dev/sda7           17246       18096     6835626   83  Linux
/dev/sda8           18097       19457    10932201   83  Linux


```

Regards
Feras

---

### Post by feras.ws on 2009-01-23
> **KIAaze said:**
> So you reinstalled it already and are asking how to reinstall it? O.o

Overwriting the old version is easy. All you have to do is install to the same partition.

[LIST]
[*]If your home directory is on the same partition as your root directory, then yes, **it will delete all your data!**
[*]If your home directory is on a separate partition, then Ubuntu 8.10 should detect it and ask you if you want to reuse it. This way, your data is safe. :)
[/LIST]

Home auto-detection info:
[http://brainstorm.ubuntu.com/idea/138/](http://brainstorm.ubuntu.com/idea/138/)
[https://wiki.ubuntu.com/RecommendSeparateHome](https://wiki.ubuntu.com/RecommendSeparateHome) (only screenshots I could find)

_If you need partitioning help:_
I'm not sure I understood your current status clearly.
Do you have terminal access? GUI access?

_If you have terminal access:_
Post the output of the following two commands:
```
sudo fdisk -l
df -h
```

"fdisk -l" will list all your partitions (sounds like "format disk" and can probably be used for that too, but with '-l', it just lists partitions. ;))
"df -h" gives an overview of where what is mounted.

_If you have GUI access:_
Run gparted and post a screenshot. :)

```

 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              11G  2.4G  7.4G  25% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  108K 1008M   1% /var/run
varlock              1008M  4.0K 1008M   1% /var/lock
udev                 1008M  2.8M 1005M   1% /dev
tmpfs                1008M  152K 1008M   1% /dev/shm
lrm                  1008M  2.0M 1006M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0             699M  699M     0 100% /media/cdrom0
/dev/sda6             9.2G  4.0G  4.8G  46% /media/disk
/dev/sda2              83G   48G   36G  58% /media/Vista
/dev/sda3              36G   23G   13G  66% /media/New Volume


```
I installed a new ubuntu on a different partition , trying to change the permissions for the old system .

Regards
Feras

---

### Post by KIAaze on 2009-01-23
It seems to me that your old home is on /dev/sda6, i.e. your data is in /media/disk. Is that correct?

Fixing your old install seems hard to me. What does it say when you boot into it and try to log in?
Do you actually get to the login window?

It would be easier to reuse your old home partition with the new install.

---

### Post by feras.ws on 2009-01-23
> **KIAaze said:**
> It seems to me that your old home is on /dev/sda6, i.e. your data is in /media/disk. Is that correct?

exactly my old system was on ./dev/sda6.
I don't get this
> 
i.e. your data is in /media/disk. Is that correct?

Regards
Feras

---

### Post by KIAaze on 2009-01-23
Well, I mean that when you boot into the new install and look into the /media/disk folder, you see your old data, no?

edit: Here's a tutorial to move home:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)
I don't have time to adapt it now, but maybe you can figure out how to reuse your existing home with it.

---

### Post by KIAaze on 2009-01-24
In case you still haven't solved your problem and want to reuse your existing /home with the new partition:

This should work assuming you reinstalled with the same username.
Disclaimer: I haven't tested it, but I think it should work.

1)Boot into new installation
2)Do the following:
```
cd /
sudo mv /home /old_home
sudo mkdir /home
sudo mount /dev/sda6 /home

```
3)Check that everything works well and you find your data in /home
4)If yes, then backup /etc/fstab
5)edit /etc/fstab by replacing the line containing /home which might look like this:
```
UUID=<long string of numbers>	/home	ext3	defaults	0	2
```
with this:
```
/dev/sda6 /home ext3 nodev,nosuid 0 2
```
6)Reboot into the new install to see if everything is ok

Other ways to change the home directory (for which you may still have to configure the mounting of /dev/sda6 first):
[http://www.spiration.co.uk/post/1294/Unix%20/%20Linux%20change%20a%20user%27s%20home%20directory%20-%20usermod](http://www.spiration.co.uk/post/1294/Unix%20/%20Linux%20change%20a%20user%27s%20home%20directory%20-%20usermod)
[http://nixtechnica.blogspot.com/2007/04/how-to-change-your-home-directory-in.html](http://nixtechnica.blogspot.com/2007/04/how-to-change-your-home-directory-in.html)

---

