---
title: "How to install XULRunner 1.9 manually?"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by CmdGabriel on 2009-10-31
Hi All,
unfortunatly the last softwareupdate crashed during XUL Runner 1.9 installation. No of the automatic programmes (software maintenance) works anymore.

sudo apt-get install -f 

tells me, that the  XUL Runner 1.9package is not working. Software update tells me, there is no update for it. 

How can I download (from Windows - since Unix isn't working with internet ;) ) and then manually install that in Ubuntu?

Your help would be really appreciated!

Thanks
Gabriel

---

### Post by kansasnoob on 2009-10-31
I don't know of a way to use Windows to do that. All I can think of is using a Live CD, and then from the Live Desktop mount & chroot the Ubuntu / (root) partition:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

**Note: you must be sure to mount the proper partition, so if in doubt post the output of "sudo fdisk -l" before proceeding!**

If you have an internet connection from the live CD the "sudo cp /etc/resolv.conf /mnt/etc/resolv.conf" command should allow you to complete the updates - I hope.

Suggested commands while chrooted into Ubuntu would be (no sudo needed while chroot):

```
apt-get update && apt-get upgrade
```

```
apt-get -f install
```

```
dpkg --configure -a
```

If any of this is at all unclear please ask for more detailed instructions before proceeding.

---

### Post by CmdGabriel on 2009-10-31
> **kansasnoob said:**
> I don't know of a way to use Windows to do that. All I can think of is using a Live CD, and then from the Live Desktop mount & chroot the Ubuntu / (root) partition:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

**Note: you must be sure to mount the proper partition, so if in doubt post the output of "sudo fdisk -l" before proceeding!**

If you have an internet connection from the live CD the "sudo cp /etc/resolv.conf /mnt/etc/resolv.conf" command should allow you to complete the updates - I hope.

Suggested commands while chrooted into Ubuntu would be (no sudo needed while chroot):

```
apt-get update && apt-get upgrade
``````
apt-get -f install
``````
dpkg --configure -a
```If any of this is at all unclear please ask for more detailed instructions before proceeding.

Hello,

thanks for answering. Do I understand it correctly: I cannot just copy this mysterios XULRunner1.9 Archive from somewhere on the internet to some special place on my harddrive and then reinstall it?

Instead I try to boot from the original Ubuntu Installdisk, look for the command line and then enter the commands above?

I have a question about:
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

This copies the resolv.conf file from the Linux-CD to HD? or is this a copy within the harddisk?
Cannot I just boot Ubuntu (booting is still working) and do it without CD? I am missing drive names (like in Windows ;-) ) to understand where the both directories etc and mnt/etc are.

Regards
Alex

---

### Post by kansasnoob on 2009-10-31
> **CmdGabriel said:**
> Hello,

thanks for answering. Do I understand it correctly: I cannot just copy this mysterios XULRunner1.9 Archive from somewhere on the internet to some special place on my harddrive and then reinstall it?

Instead I try to boot from the original Ubuntu Installdisk, look for the command line and then enter the commands above?

I have a question about:
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

This copies the resolv.conf file from the Linux-CD to HD? or is this a copy within the harddisk?
Cannot I just boot Ubuntu (booting is still working) and do it without CD? I am missing drive names (like in Windows ;-) ) to understand where the both directories etc and mnt/etc are.

Regards
Alex

I'm not aware of anyway you can do that from Windows.

I'll give you some very detailed instructions if you'll boot the Live CD and choose Try Ubuntu without changes to disc. That's what we call working from the live Desktop.

Once in the Live Desktop I need to see the output from Terminal (Applications > Accessories > Terminal) of this command:

```
sudo fdisk -l
```

BTW that's a lower case L at the end.

---

### Post by CmdGabriel on 2009-11-01
> **kansasnoob said:**
> 
```
sudo fdisk -l
```BTW that's a lower case L at the end.

I am impressed of the live cd capability.

Output is

  	 	 	 	 	 	  Disk /dev/sda: 250.0 GB, 250059350016 bytes 
 255 heads, 63 sectors/track, 30401 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0xfa80fa80 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS


  
 Disk /dev/sdb: 160.0 GB, 160041885696 bytes 
 255 heads, 63 sectors/track, 19457 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0x89e189e1 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdb1               1        7101    57038751    7  HPFS/NTFS 
 /dev/sdb2            7102       19457    99249570    5  Extended 
 /dev/sdb5            7102       18949    95169028+  83  Linux 
 /dev/sdb6           18950       19457     4080478+  82  Linux swap / Solaris
 
The first one in my Windows - Boot one.
The second hard drive contains an NTFS data partition and the Ubuntu boot partition.

Regards
Alex

---

### Post by CmdGabriel on 2009-11-01
*mounting local drive sdb5:*

[B]ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get update
[/B]Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic Release.gpg                           
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic Release
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/restricted Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/main Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/restricted Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/universe Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/universe Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done

**root@ubuntu:/# apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package xulrunner-1.9 needs to be reinstalled, but I can't find an archive for it.

**root@ubuntu:/# apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package xulrunner-1.9 needs to be reinstalled, but I can't find an archive for it.

**root@ubuntu:/# dpkg --configure -a**
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9.0.15+nobinonly-0ubuntu0.9.04.1); however:
  Version of xulrunner-1.9 on system is 1.9.0.14+build2+nobinonly-0ubuntu0.9.04.1.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-branding:
 firefox-3.0-branding depends on firefox-3.0 (= 3.0.15+nobinonly-0ubuntu0.9.04.1); however:
  Version of firefox-3.0 on system is 3.0.14+build2+nobinonly-0ubuntu0.9.04.1.
dpkg: error processing firefox-3.0-branding (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9-gnome-support
 firefox-3.0-branding

---

### Post by kansasnoob on 2009-11-01
Try running the following command and post any output here:

```
apt-get update && apt-get install --reinstall xulrunner-1.9.1
```

---

### Post by CmdGabriel on 2009-11-01
Hey,
that creates same error message:

[B]root@ubuntu:/# apt-get update && apt-get install --reinstall xulrunner-1.9.1
[/B]OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic Release.gpg
Hole:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/main Translation-de [412kB]
OK   [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-de                
OK   [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-de
OK   [http://archive.canonical.com](http://archive.canonical.com) karmic Release          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-de       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-de         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-de       
OK   [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                        
OK   [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                      
OK   [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages 
OK   [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
OK   [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources  
OK   [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
OK   [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hole:2 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/restricted Translation-de [897B]
Hole:3 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/universe Translation-de [1437kB]
OK   [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources               
OK   [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages            
OK   [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources     
Hole:4 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/multiverse Translation-de [32,1kB]
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates Release.gpg 
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/main Translation-de
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/restricted Translation-de
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/universe Translation-de
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/multiverse Translation-de
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic Release
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates Release  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/main Packages                         
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/restricted Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/main Sources     
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/restricted Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/universe Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/universe Sources 
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/multiverse Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/multiverse Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/main Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/restricted Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/main Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/restricted Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/universe Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/universe Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/multiverse Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/multiverse Sources
Es wurden 1883kB in 3s geholt (503kB/s)                   
Paketlisten werden gelesen... Fertig
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
[COLOR=Red]E: Das Paket xulrunner-1.9 muss neu installiert werden, ich kann aber kein Archiv dafür finden.[/COLOR]

Where the red error message is the same as above: he doesn't find the xulrunner archive ("but I can't find an archive for it.") . Sorry for switching to German in the current boot...

Is it possible to install Ubuntu from live cd over the current installation without killing the data files? (eg. from email)

Regards
Gabriel

---

### Post by kansasnoob on 2009-11-01
Are you able to browse the internet from the Live Desktop?

That is, are you posting these messages from the Live desktop?

---

### Post by kansasnoob on 2009-11-01
> Is it possible to install Ubuntu from live cd over the current installation without killing the data files? (eg. from email)


No!

---

### Post by CmdGabriel on 2009-11-01
> **kansasnoob said:**
> Are you able to browse the internet from the Live Desktop?

That is, are you posting these messages from the Live desktop?

Yes, that why I think live desktop is amazing. ;-)
But how could I get these XUL RUnner Archvies on my Harddisk?

---

### Post by kansasnoob on 2009-11-01
Sorry to just disappear but I had an unexpected dinner invite and being an old guy that lives alone, I never pass that up!

Anyway, I suspected that you were posting from the Live CD but wanted to be sure. I think what's happening is somewhat explained here:

[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)

So, I'm thinking I'd boot back into the regular desktop and go to Software Sources and try the main server.

---

### Post by CmdGabriel on 2009-11-02
> **kansasnoob said:**
> Sorry to just disappear but I had an unexpected dinner invite and being an old guy that lives alone, I never pass that up!

Anyway, I suspected that you were posting from the Live CD but wanted to be sure. I think what's happening is somewhat explained here:

[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)

So, I'm thinking I'd boot back into the regular desktop and go to Software Sources and try the main server.
 Hi, I looked up the manual. The problem is that the "software sources" application does not work - it stops during "bulding dependencies" with the message about (missing archive)  I think I need either manually kill XULRunner and its dependent software from the repository list (how?) or to download XULRunner Archive manually fromsomewhere.  I found these links: [http://ubuntuforums.org/archive/index.php/t-1148436.html](http://ubuntuforums.org/archive/index.php/t-1148436.html) [http://ubuntuforums.org/archive/index.php/t-1145078.html](http://ubuntuforums.org/archive/index.php/t-1145078.html)  But I cannot "translate" it into my solution, since I don't know which depencies XUL Runner has and because I am pretty new to Linux :-)  Regards Alex

---

### Post by kansasnoob on 2009-11-02
Well, if you can actually boot into the OS again (not using chroot) you might be able to do something like install "seamonkey-browser" which doesn't depend on xulrunner.

```
sudo apt-get install seamonkey-browser
```

Then using Seamonkey go here and download the .deb (bottom of page choose either i386 or 64 bit):

[http://packages.ubuntu.com/karmic/xulrunner-1.9.1](http://packages.ubuntu.com/karmic/xulrunner-1.9.1)

And see what happens.

Something else that would be nice is if I could see your sources.list. You can get it by running:

```
cat /etc/apt/sources.list
```

Then paste it here.

---

### Post by kansasnoob on 2009-11-02
Another thought. If you'd mount and chroot again from the live CD we could fairly easily rebuild the sources.list.

Once you're chrooted into Karmic back up the sources.list:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Then using your browser from the live desktop go here:

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

I've used that and it's safe. 

Select country (or if you want to use the Main Repo select no country) and select Release = Karmic, and for now I'd just check everything in Ubuntu Branches, Ubuntu Updates, and Ubuntu Partner Repos. We don't want to mess with 3rd party stuff right now.

We will edit some stuff in Software Sources later if this works.

Then just click on Generate List.

It'll look something like this:

> #############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse 
deb-src [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-security main restricted universe multiverse 
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse 
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-proposed main restricted universe multiverse 
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse 
deb-src [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-security main restricted universe multiverse 
deb-src [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse 
deb-src [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-proposed main restricted universe multiverse 
deb-src [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

**In fact you could just use that sources.list if you want to use the Main Repo.**

Then go back to our chroot environment and run:

```
gksudo gedit /etc/apt/sources.list
```

Click on Edit > Select all and then Cut. Then copy & paste the new sources.list to that file, click on Save, then File > Quit.

Then, just to be sure the changes were saved, I always run:

```
cat /etc/apt/sources.list
```

just to be sure the changes were saved.

If it looks right then run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

And see what happens.

I should have thought of this sooner!

---

### Post by CmdGabriel on 2009-11-04
I think, I understood, what to do... but I cannot.
I am not able to edit the file.

root@ubuntu:/# **gksudo gedit /etc/apt/sources.list**
No protocol specified

An I cannot use one of the other text editors, since the sources.list belongs to root and not to me... :-)

---

### Post by kansasnoob on 2009-11-04
> **CmdGabriel said:**
> I think, I understood, what to do... but I cannot.
I am not able to edit the file.

root@ubuntu:/# **gksudo gedit /etc/apt/sources.list**
No protocol specified

An I cannot use one of the other text editors, since the sources.list belongs to root and not to me... :-)

Sorry, that was my bad. Sometimes I goof. You'll have to use nano which is also a text editor but it's a bit more difficult to use so read closely.

Once again mount and chroot sdb5 (I think that's right, isn't it? If I have sdb5 wrong tell me.) then run this command:

```
nano /etc/apt/sources.list
```

It's going to look quite different to you (example):

[ATTACH]134747[/ATTACH]

Navigating nano is a bit more difficult (but not as bad as vi). You'll see that you can't "cut" text like you can using gedit so you'll have to use the arrow keys.

In this case press the down arrow key which will take you all the way to the last line of text, then use the right arrow key to take you to the end of that line, then use the backspace key to delete all of the text. It'll take a while, but don't worry, it'll stop when all of the text is deleted.

Luckily it does allow pasting (unlike vi) so copy-n-paste that new sources.list:

> ################################################## ###########
################### OFFICIAL UBUNTU REPOS ###################
################################################## ###########

###### Ubuntu Main Repos
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse
deb-src [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse

###### Ubuntu Update Repos
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-security main restricted universe multiverse
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-proposed main restricted universe multiverse
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-security main restricted universe multiverse
deb-src [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse
deb-src [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-proposed main restricted universe multiverse
deb-src [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner 

With the cursor blinking at the end or beyond the bottom of the new sources.list you must press the Ctrl and x keys simultaneously which will result in this (look at the bottom):

[ATTACH]134748[/ATTACH]

So type y indicating yes. Then at the bottom it'll ask you "file name to write: /etc/apt/sources.list" which will be correct so just hit Enter. You'll see you're back in terminal, so run the command:

```
cat /etc/apt/sources.list
```

To be sure the changes took. They will have. I have faith in you.

Then resume the rest:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Sorry I messed up on the text editor thing (gksudo was also wrong). You can kind of see why I'd rather use gedit whenever possible. I'll have to explore why using gedit doesn't work with that in Karmic.

Remember to "exit" and unmount when done.

---

### Post by kansasnoob on 2009-11-05
I was thinking about this again earlier and just in case it's needed I built a more "correct" sources.list (Main repos used):

> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.4)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe


---

### Post by CmdGabriel on 2009-11-12
Hi,
I am back :) -  a few days lots of work  ... but now i am back...
I booted live cd and connected to my desktop hd as before.
I have exchanged the list as above.

Here is what my computer says:

root@ubuntu:/# **apt-get update && apt-get dist-upgrad**
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                              
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Packages
  404 Not Found [IP: 91.189.88.134 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Packages
  404 Not Found [IP: 91.189.88.134 80]
W: Not using locking for read only lock file /var/lib/apt/lists/lock
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/binary-amd64/Packages)  404 Not Found [IP: 91.189.88.134 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
W: Not using locking for read only lock file /var/lib/dpkg/lock

///

I trieed to exchange the file with a new generated German one, but it does not work. Now the systems insists that the file is read only ...

Regards
Alex

---

### Post by kansasnoob on 2009-11-13
**Just thinking out loud here. Lets consider alternatives, OK?**

I think it's time to revisit this thought:

> Is it possible to install Ubuntu from live cd over the current installation without killing the data files? (eg. from email)

As I said earlier the direct answer is no, but there are two ways we can "reinstall" and save your data:

Option #1: Create "parallel" partitions for a new install, installing to them using the manual install option, and then transferring your data to the fresh install. After which we can delete the "bad" install and expand the new "Home" partition to use that space.

From your fdisk -l:

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa80fa80

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30400 244187968+ 7 HPFS/NTFS



Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89e189e1

Device Boot Start End Blocks Id System
/dev/sdb1 1 7101 57038751 7 HPFS/NTFS
/dev/sdb2 7102 19457 99249570 5 Extended
/dev/sdb5 7102 18949 95169028+ 83 Linux
/dev/sdb6 18950 19457 4080478+ 82 Linux swap / Solaris

I imagine that sdb looks similar to this:

[ATTACH]136054[/ATTACH]

*image courtesy of: [http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)*

Basically what we would do is shrink sdb5 to the right and create two new partitions to the left of it (one for / and another for /home) to install to. Then we'd transfer the data from sdb5 to the new install, but we'll get into specifics after making a decision.

Option #2: Transferring your data to the NTFS data partition as a backup and then transferring it back to the new install. It's kind of up to you. Do you normally access data on the NTFS data partition from Ubuntu?

Either way we'd want to use the "manual" method of installation so we can create a separate Home partition. That way in the future you can reinstall with no real worries.

Before deciding I should see the following and have a few questions answered:

(1) A screen-shot of Gparted from the Live CD (of sdb) like that above. That will tell me a lot: specific partition size, free space, etc.

(2) The results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

That will tell me where grub is currently installed, etc. The last thing we need to do now is install grub to the mbr of the wrong drive!

(3) As mentioned above, do you normally access (read and write) data on the NTFS data partition from Ubuntu? The program ntfsprogs is very helpful with that, but it also allows you to delete and otherwise destroy data or even program files in NTFS drives/partitions. An alternative is ntfs-config, anyway if you normally access files on the NTFS data partition already you probably already know how to do so.

(4) How much and what kind of data are we saving from Ubuntu? What email program(s) do you use?

(5) What version of Ubuntu would you choose to install? IMO 9.10 has been far too problematic, for me 9.04 was much more stable.

We should also consider what file system type to use, consider this (from the Ubuntu 9.10 release notes):

> There have been some reports of data corruption with fresh (not upgraded) ext4 file systems using the Ubuntu 9.10 kernel when writing to large files (over 512MB). The issue is under investigation, and if confirmed will be resolved in a post-release update. Users who routinely manipulate large files may want to consider using ext3 file systems until this issue is resolved. 

Also 9.10 installs grub2 by default and it's been horribly problematic with multiple drive systems. I guess I never even asked, was this an upgrade from 9.04 to 9.10? If so how had 9.04 been working for you?

I may think of more after I see your answers and hear your thoughts on this. Sorry you've had so much trouble.

Just BTW I read this in the release notes this morning:

> Upstart jobs cannot be started in a chroot because upstart acts as a service supervisor, and processes within the chroot are unable to communicate with the upstart running outside of the chroot (430224). This will cause some packages that have been converted to use upstart jobs instead of init scripts to fail to upgrade within a chroot. Users are advised to configure their chroots with /sbin/initctl pointing to /bin/true, with the following commands run within the chroot:

dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

That may explain why we encountered problems, but I'm thinking you're beyond disgusted at this point and would rather reinstall. I'm personally pretty tired of trying to tackle Karmic problems.

---

### Post by CmdGabriel on 2009-11-13
Hi,

thanks for all your help so far. The main problem here for me is, that I just don't really understand, what was really wrong... (to a more detailed level than "it doesn't work).

So the easiest thing seems to be to recover all important data files and then start from scratch (directly on the right partition). So option #2.

(1,2)Grub is installed on the linux partition. So I imagine, that won't be a problem if I just overwrite it.

(3, 4) NTFS access is transparent and not  a problem at all so far. I had full read/write access.
What I can do of course is to copy all important data files "away" to my Windows disk.
The only files I am not sure, if I can catch them correctly are the Evolution Mail data files (email, contacts). 

Everything else shouldn't be too much work to reinstall and to setup the users again.

BTW: In former Windows times I had to reinstall a few times, too.

(5) I guess I stay with 9.04 for a while ;-) I will just go back to what I had.
I have never imagined that this update will be problematic, after all former software installations where so easy.

I would even guess: If you help me with my mail files, than I could be able to do the rest on my own. 

And in fact - I learned a lot the past few days ;-)


Regards
Gabriel

---

### Post by kansasnoob on 2009-11-14
> **CmdGabriel said:**
> Hi,

thanks for all your help so far. The main problem here for me is, that I just don't really understand, what was really wrong... (to a more detailed level than "it doesn't work).

So the easiest thing seems to be to recover all important data files and then start from scratch (directly on the right partition). So option #2.

(1,2)Grub is installed on the linux partition. So I imagine, that won't be a problem if I just overwrite it.

(3, 4) NTFS access is transparent and not  a problem at all so far. I had full read/write access.
What I can do of course is to copy all important data files "away" to my Windows disk.
The only files I am not sure, if I can catch them correctly are the Evolution Mail data files (email, contacts). 

Everything else shouldn't be too much work to reinstall and to setup the users again.

BTW: In former Windows times I had to reinstall a few times, too.

(5) I guess I stay with 9.04 for a while ;-) I will just go back to what I had.
I have never imagined that this update will be problematic, after all former software installations where so easy.

I would even guess: If you help me with my mail files, than I could be able to do the rest on my own. 

And in fact - I learned a lot the past few days ;-)


Regards
Gabriel

Well, I don't use Evolution but I found this:

[https://answers.launchpad.net/ubuntu/+source/evolution/+question/5749](https://answers.launchpad.net/ubuntu/+source/evolution/+question/5749)

The part about shutting down Evolution via the command "evolution --force-shutdown" does make sense to me because I've encountered problems if I've mistakenly left an application (ie: Firefox or Opera) open when I created a backup.

What I commonly do to create a backup of home is to simply go to Places > Home, then on that page I click on the up arrow at the top of the page. This displays all of the <user-name> folders and a folder named "lost & found".

So I simply right click each <user-name> folder, then click properties to check the size just so I know that my destination size is appropriate for the backup, then I click copy. Then I simply switch to the desktop with my destination drive/partition and paste.

I repeat that with each <user-name> folder until I'm done and then of course I check the integrity of the copies by looking at the contents of each backed up folder after I'm done just to be sure that all was copied properly. 

The only problems I've encountered are that if I goof and have an app like Firefox running at the time I create the backup then Firefox will either refuse to run on the fresh install or it'll automatically start every time I reboot, or once in a while the permissions of certain folders will need to be fixed by right clicking the folder after restored (although that more often occurs if the backup is made on a CD or DVD).

Regarding grub I always like to be cautious. Generally during a default installation grub will install to the mbr of the first drive in the boot sequence (ie: sda or (hd0) in grub lingo). That's why I thought it would be wise to run the Boot Info Script from the Live CD.

It shows a lot of info, only some of which you'd care about, but specifically it would show if the Windows boot-loader is still installed to the mbr of sda, and which mbr grub is installed to. Example:

> => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

Of course if you choose to install 9.10 it now installs grub2 by default which may or may not work for you. It has been problematic in some, but not all, multi-drive installations. No sweat though, I wrote a HowTo for reverting to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Finally regarding a separate /home partition. It's really simple, and should you ever need to reinstall again you shouldn't have to worry about losing data (although it's always a bit risky to not have a backup). 

Once you have everything backed up and you're ready to install just boot the Live CD and from the Live Desktop go to System > Administration > Gparted (aka: Partition Editor). You'll commonly have to right click on the SWAP partition and click on swapoff.

Your Ubuntu partition appears to be sdb5 so right click that and choose delete. Then right click the new blank area and choose "new". Move the slider to the left so the new partition is 6GB to 8GB. That will be your new / (aka: root) partition. (I've seldom seen a / partition grow beyond 4GB).

Then right click on the remaining space and select "new" again. (We don't care right now what file system type you choose as we'll get to decide that again during installation and nothing need be changed regarding SWAP). Then just click on the green check-mark to apply.

When that's done you'll have a new sdb5 and probably a new sdb7, since SWAP is sdb6. It does not matter that the numbers are not sequential on the drive. Whatever those numbers are you want to make a note of because that's where you'll "manually" choose to install "/" and "/home".

Now you should be ready to install, I'll be assuming that the new partitions are sdb5 and sdb7, if that's wrong substitute the proper #'s. Exit Gparted and double click on the Install icon on the desktop. When you get to this screen:

[ATTACH]136184[/ATTACH]

Be absolutely certain to select Specify partitions manually (advanced). That will take you to this screen:

[ATTACH]136185[/ATTACH]

So you'll see why knowing your drive/partition numbers is needed. If I guessed the new partition #'s correctly you'll select sdb5 and then click on Edit partition which will bring up a smaller screen where you'll select some options:

*New partition size (this option is not present in all versions of Ubunu): We already made the partitions the right size with Gparted so you should be able to accept the default here.

*Use as: This is where we specify file system type, either ext3 or ext4 should be fine IMO.

*Format the partition: Yes! make sure that it ticked!

*Mount point: This is important! Since this is the root partition we choose "/"! NOT /boot, just /.

Then simply click on OK and wait for ubiquity to register the changes.

Now we repeat those steps for sdb7 (remember I'm somewhat guessing about partition #'s) only with one big difference:

*New partition size: As above default size should be correct.

*Use as: Same as above, choose either ext3 or ext4.

*Format the partition: Yes!

*Mount point: This time we want "/home". That's of major importance!

Again click on OK and wait for ubiquity to register the changes.

No changes need be made to SWAP.

Now you'll simply click on forward and you'll be presented with the screens where you enter name, password, etc. and whether or not you wish to migrate stuff (which I never do).

Then you get the last chance to "go back" and change things:

[ATTACH]136190[/ATTACH]

It should show that sdb5, sdb7, and sdb6 are going to be formatted correctly. This is your last chance to change your mind! You'll also notice in the lower right hand corner of that screen there's an Advanced button, you'd click on that if you wanted to see (or change) where grub is going to be installed.

Now, why is it worth doing this? First of all you get to decide exactly where Ubuntu is going to be installed, but if you should ever end up with a broken Ubuntu again you can repeat the steps above with one simple change and keep the data on your /home partition.

**That one simple "change" is: you would still choose to edit the /home partition, just be sure to stay with the current file system type, and DO NOT check the format box!**

Just to repeat myself: You would treat / just as above, but when it comes to /home you would be certain to keep the current file system type and NOT format. That way your data **[COLOR="Red"]should[/COLOR]** remain intact!

I highlighted should because the best laid plans sometimes go awry.

Please ask more questions if you're the least bit confused by this and regarding Evolution, unless you're sure, start a new thread asking how to properly back up Evolution before reinstalling.

Sorry it came to this!

---

### Post by CmdGabriel on 2009-11-21
Hey,

it's done!!! Many thanks. Today Ubuntu works again for me - including all old emails..
I even managed to find out how to point GRUB in the MBR to the new location.. :-)

Many, many thanks for all your help!
Gabriel

---

