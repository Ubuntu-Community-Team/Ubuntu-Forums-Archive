---
title: "How to get Wine to read more than one CD when installing a game"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by Carolla on 2009-06-10
I have Wine and Play on Linux and am attempting to install Civ IV. Things go fine until I need the second CD. Then I get an error saying the CD is in use and I cannot open the drive to change CD's. I am using Wine through Play on Linux, if I understand that correctly. Any help would be appreciated.

---

### Post by 4Orbs on 2009-06-10
You could make ISO copies of the cd's and save them in your home folder, then install the game from a virtual drive. I use gmount-iso to mount and unmount the drive (you gotta configure wine to work with the drive before installing the game). This way you won't need to use the real cd drive in the installation process. Virtual drives are groovy.

---

### Post by Carolla on 2009-06-10
Isn't it easier to just use the CD's? I'm afraid that might be an old Windows preconception that tossing a CD in the drive and just using it is the easiest and fastest thing. I'd rather not try to burn iso's from a commercial game CD in order to install it. Not too sure if that would even work?

Anyone have any ideas - there must be something in the configuration of either Wine or PlayOnLinux that would allow me to switch CD's while installing a game? Should I just try it again?

---

### Post by Nythain on 2009-06-10
ummm... make sure you arent in the mounted media anywhere... you could try to manual unmount it with a
sudo umount /dev/that/is/your/cdrom

i havent tried installing Civ4 with discs, i always just mount the iso at whatever location, then unmount it when i need the next disc, and mount the next disc in the same spot.

Civ4 will install just fine from iso, like i said, i do it all the time (i really hate cd/dvd media, scratches, corrosion, gets lost, etc)

---

### Post by Carolla on 2009-06-10
> **Nythain said:**
> ummm... make sure you arent in the mounted media anywhere... you could try to manual unmount it with a
sudo umount /dev/that/is/your/cdrom

i havent tried installing Civ4 with discs, i always just mount the iso at whatever location, then unmount it when i need the next disc, and mount the next disc in the same spot.

Civ4 will install just fine from iso, like i said, i do it all the time (i really hate cd/dvd media, scratches, corrosion, gets lost, etc)

You play Civ IV in unbuntu? I'm afraid I am a total noob and that is the one thing I really need to be able to do before I can just change OS. I play all the time with my friends online and am not willing to give that up. I'm not even sure what you mean by mounting and unmounting drives. You give a line of code, not sure where to enter it and what it would do if I did, or when to enter it! 

Also... my read/write CD drive is in another computer which is only partly functional (been upgrading 'puters around here lately) so it's a bit awkward writing an iso - will Nero do that? 

How do you set up ubuntu to run Civ IV? Are you willing to hold a total noob's hand through the process? :)  If not, that's ok, I'll figure it out eventually - I'm stubborn.

---

### Post by 4Orbs on 2009-06-10
> Isn't it easier to just use the CD's?
Actually, initially quicker but not easier. Other than the initial setup and configuration (maybe three minutes) and time spent creating the ISO's (have dinner while you wait), virtual drives are superior. And when you have the game playdisc on ISO, you never need to use the plastic cd again... or open the cd tray either.

---

### Post by Carolla on 2009-06-10
> **4Orbs said:**
> Actually, initially quicker but not easier. Other than the initial setup and configuration (maybe three minutes) and time spent creating the ISO's (have dinner while you wait), virtual drives are superior. And when you have the game playdisc on ISO, you never need to use the plastic cd again... or open the cd tray either.

Well, as I asked Nythain, I'm glad for any help but new as new can be. I'm still picking up the vocabulary even. Any help with mounting and unmounting the CD's (or iso's) would be greatly appreciated though it would have to be pretty much written for the idiot at this point. :)

---

### Post by bodhi.zazen on 2009-06-10
Wine has come a long ways, but some things are best or only managed from teh command line.

When you put a CD into the CD drive it is automatically mounted to /media/cdrom

so ...

Open a terminal and :

```
sudo umount -f /media/cdrom
```

Now open the CD drive and change CD. The new CD should be recognized and run out of the box. If not manually mount it :

```
mount /media/cdrom
```

---

### Post by dje on 2009-06-10
see [here]("http://wiki.winehq.org/eject") (info on how to use wine eject) ;)

dje

---

### Post by Carolla on 2009-06-10
Also, should I try to make iso's from my CD's from within ubuntu? If so, how do I do that? 

I do have dinner hours... :)

---

### Post by yaroto98 on 2009-06-10
I agree with dje

```
#wine eject
```

it always worked for me.

---

### Post by 4Orbs on 2009-06-10
Dude, we Americans, by law, are not permitted to make a 1:1 ISO copy of games of which we have legitimate ownership using Brasero. So I can't tell you how to click the buttons. But to use an ISO disc in Wine:

1. Open the Synaptic Package Mgr, find gmountiso and mark it for installation. Then click the "Apply" button at the top of Synaptic. This installs Gmount-iso which can then be found in the System Tools menu.

2. Create a new empty folder in your personal home folder and name it ISO-mount (or whatever name you prefer).

3. Open Gmount-iso and select the first ISO you need for installation. Then for the mount point select the new folder you created. Then click the mount button. It should mount the ISO with no problem if you know your admin password.

4. Open the Wine Configuration tool and select the "Drives" tab. Then click on "autodetect" which will list all the drives it detects.

5. Click on the "Add" button. On the "Add" line, click on the file button to navigate thru the tree menu to find the new folder you created. That folder will be specified as the new added drive.

6. Still on the wine config tool, click on the "Advanced" button located next to the new added drive name. Open the dropdown box to choose "Type" as cdrom. This tells wine to use the new folder as a cd drive (virtual).

7. Click "Apply", "Save" and close the wine config mgr.

8. Now go to the new folder with your file manager and open the folder. Inside you should find the contents of the mounted ISO. Find the file that is named install.exe or setup.exe or game.exe and right click on it to open the "Properties" box. Click on the "Open With" button and select "Wine Program Loader" and close the properties box, then double click the install.exe file and wine should open the splash screen for the game installer.

9. When it comes time to switch to the second cd, pull the Gmount-iso up from the taskbar and click unmount to unmount the first cd, then click "Select" and navigate to the second cd, select it and click mount then pull the installer back to the forefront and click "Continue" to complete the installation.

10. Remount the playdisc if it is required to play. Then go to the Wine menu inside the Applications menu and you should find you new game listed and click on the game title to begin play. NOTE: you might need to log out of your desktop and log back in before the game will show up on the menu.

11. Tomorrow, when you want to play again, just use Gmount-iso to remount the game ISO and play 'til you get hungry for a peanut butter sandwich.

P.S. I am assuming you have already installed all the necessary audio/video codecs required for media playback in Ubuntu. Also the necessary Hardware driver for your graphics card.

---

### Post by Carolla on 2009-06-10
Installed the necessary devices... well, no, I'll have a whole new learning curve for that! lol I'm just working on this an hour or two a day in between the other stuff I want to do, such as actually playing civ on my windows boot. Not to mention talking on the phone, reading emails, doing chores, cooking dinner and working a bit too. It may take me a while to get it up and running, but no worries!

---

### Post by 4Orbs on 2009-06-10
It takes more time to read it than actually do it. The Wine configuration is just a one-time thing. After it's set up you can use the same folder as the virtual drive for any other games you play. You can have only one game at a time mounted on it. But from then on, all you need is Gmount-iso and the new game ISO. Don't be put-off by the length of my post. Once you use a virtual drive successfully, I promise you will be delighted. Oh, if you don't have all the media stuff for Ubuntu installed, your games probably won't play regardless how you install them.

---

### Post by Carolla on 2009-06-10
> **4Orbs said:**
> It takes more time to read it than actually do it. The Wine configuration is just a one-time thing. After it's set up you can use the same folder as the virtual drive for any other games you play. You can have only one game at a time mounted on it. But from then on, all you need is Gmount-iso and the new game ISO. Don't be put-off by the length of my post. Once you use a virtual drive successfully, I promise you will be delighted. Oh, if you don't have all the media stuff for Ubuntu installed, your games probably won't play regardless how you install them.

Ok, read through it and am working on it now. Of course first I'll need the ISO to mount, which I am also working on atm. You just put all the ISO's in the same folder and mount/unmount as you need them? 

BTW thanks for the clear explanation.

---

### Post by 4Orbs on 2009-06-10
Just to add more scraps of confusion: In Windows some games can be played only if the playdisc is using the same cd drive as was used to install the game. While other games might play ok using a different drive than was used to install them. I don't know if this behavior carries over to Ubuntu, but you might be able to install a game using the cd drive and then play that game using an ISO copy of the playdisc mounted on a virtual drive. Thus you would only need to copy one disc rather than two or more.

I keep my game ISO's all in one folder on a separate partition used solely for multimedia storage, which I also share with the Windows system. I use virtual drives for gameplay in Windows too, and use the same ISO's on either system.

---

### Post by Carolla on 2009-06-10
> **4Orbs said:**
> Just to add more scraps of confusion: In Windows some games can be played only if the playdisc is using the same cd drive as was used to install the game. While other games might play ok using a different drive than was used to install them. I don't know if this behavior carries over to Ubuntu, but you might be able to install a game using the cd drive and then play that game using an ISO copy of the playdisc mounted on a virtual drive. Thus you would only need to copy one disc rather than two or more.

I keep my game ISO's all in one folder on a separate partition used solely for multimedia storage, which I also share with the Windows system. I use virtual drives for gameplay in Windows too, and use the same ISO's on either system.

So the ISO's can be used by Windows too? Do they need to be in a separate partition to do that? I'm using 30 gigs of a 80 gig drive for unbuntu, the rest is empty. How do you set up that partition? (I am using a dual boot system for now.)

---

### Post by 4Orbs on 2009-06-10
You could store the ISO's on your Windows system and play them in Ubuntu since Ubuntu can read and write to NTFS. To do that you only need to mount the Windows partition on Ubuntu (Ubuntu is already set up for that). But to do it the other way around you have to install a special driver in Windows so it can read from an EXT3 (Linux) partition. I personally prefer a completely separate storage partition formatted as NTFS to share files between both. Since you already dual boot, you should have enough experience  repartitioning the hard drive to create an extra storage partition. You can have only four primary partitions on a hard drive, and dual booting means you already have at least three on yours. If that's the case, then you only need to shrink one partition down to leave some GB of unallocated space on the drive. Then create a storage partition from that empty space. If the new partition is formatted as NTFS, Windows will automatically mount it at boot up. You can also use Windows to defragment it when necessary. To mount the partition on Ubuntu, I use the Storage Device Manager (available through Synaptic as pysdm). For me the pysdm is more convenient than other methods of mounting a storage partition (or Windows partition, for that matter) because I can set folder permissions without having to use the command line.

---

