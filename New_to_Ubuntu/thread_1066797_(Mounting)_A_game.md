---
title: "(Mounting?) A game"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by AllRadioisDead on 2009-02-11
Hi, I've just downloaded a game, and the description said it needed something like Daemon tools or "Alcohol" to "mount". I've never done this before on windows, so I'm not sure what these programs do. I checked out the websites for the two above software programs, and they appear to be windows only, so I'll need an equivalent for linux. The game I downloaded needs 2 CD's, so here is the content of my download.

My download contained:

-CD1.rar
--file.mdf
--file.mds

-CD2.rar
--file.CCD
--file.cue
--file.img
--file.sub

Could someone please help me out? Thanks!

---

### Post by finer recliner on 2009-02-11
all you need is the .img file.


follow this tutorial to mount it in linux:

[http://www.ubuntu-unleashed.com/2008/04/howto-mount-isos-in-ubuntu-easy-way.html](http://www.ubuntu-unleashed.com/2008/04/howto-mount-isos-in-ubuntu-easy-way.html)

---

### Post by AllRadioisDead on 2009-02-11
> **finer recliner said:**
> all you need is the .img file.


follow this tutorial to mount it in linux:

[http://www.ubuntu-unleashed.com/2008/04/howto-mount-isos-in-ubuntu-easy-way.html](http://www.ubuntu-unleashed.com/2008/04/howto-mount-isos-in-ubuntu-easy-way.html)

Thank you!

---

### Post by AllRadioisDead on 2009-02-11
Hi, sorry for double posting but I'm not clear about something. You mentioned I only need the .img file, but I have 2 CD's, and there's only 1 img file, how will this work?

---

### Post by rgb96 on 2009-02-11
Try just mounting the .img file and running it. It probably is an image of all the files you will need to install and run the game.

---

### Post by AllRadioisDead on 2009-02-11
I don't think so, the first CD has a 700mb MDF file on it.
Here are the instructions:
1. Unzip the files you've just downloaded

2. Now run daemon tool or alcohol 120% and mount ".mdf", it will auto play and you should see install, when you click install it will ask for the serial number. You can find the serial in CD1 folder "serail"., half way installing it will prompt you to insert disk 2, now mount "SIMCITY 4 DELUXE EDITON CD2.img" you can find this on cd2 folder.

---

### Post by rgb96 on 2009-02-11
Okay then. That tutorial is named "Howto: Mount .ISO, .IMG, .BIN, .MDF, and .NRG in Ubuntu Linux The Easy way " so just follow the instructions, except with the .mdf at first. Then when it asks you to change then mount the .img.

---

### Post by dannyboy79 on 2009-02-11
well is this a windows game? if it is, are you installing this using wine or some windows emulator?

---

### Post by AllRadioisDead on 2009-02-11
> **dannyboy79 said:**
> well is this a windows game? if it is, are you installing this using wine or some windows emulator?
Playonlinux has a installer for it, so I'm using wine.

---

### Post by 4Orbs on 2009-02-11
There is an app in the Ubuntu repositories that is similar to Daemon tools and makes mounting an unmounting iso files a snap. It's called gmount-iso and can be installed by Synaptic Package Mgr. If you install this, you must first configure wine to work with a new mount point for the virtual drive. Here are the steps I take:
1. Create a new folder in your home (your home, not the system Home) folder and name it whatever you choose. I named mine virt0.
2. Open gmount-iso and click on the top button to locate the iso file you wish to mount.
3. Click on the second button to locate your mounting point (the virt0 folder)
4. Click on the "Mount" button, you'll be asked the admin password.
5. Once the iso is mounted, open the wine configuration gui. Select the "Drives" tab at the top. Click the auto-detect to populate the list of current available drives (cd, dvd, etc.).
6. Click on "add" and then click the little folder button to navigate to the new folder you created in your home directory. The new folder is now assigned as the new mount point (drive).
7. Click the "Advanced" button to expand your options. Click on "Type" and select cdrom from the dropdown menu.
8. Click ok to finish the configuration and close the config utility.
9. Use your file mgr (Nautilus) to open the new folder you created (which still has the iso mounted to it) and double click the install.exe file. You should now be presented with the game installation program.
10. When it comes time to insert disc 2 of the install, click the "Unmount" button on gmount-iso, then click the top button to navigate to the second iso image to be mounted. Click mount, then click continue on the game install program.

EDIT: As the above poster stated, you need to first unzip or un-rar (extract) your two downloaded files.

---

### Post by AllRadioisDead on 2009-02-11
Hi, I'm having some trouble.
I've tried Acetoneiso2 and furiusisomount, but when the installer asks for the second disc, it can't find it. I made sure both discs were mounted, is this a wine problem? (When I try and unmount the first disc when it prompts the second, it says that the disc can't be unmounted because it's busy.)

---

### Post by 4Orbs on 2009-02-11
Use the same drive for both discs, first one then the other, then the first again if required. Don't mount them both at the same time.

---

### Post by AllRadioisDead on 2009-02-11
> **4Orbs said:**
> Use the same drive for both discs, first one then the other, then the first again if required.
I believe furiusisomount is mounting them both in home/myname, they're both in their individual folders though. I can't get it to detect the second disc.

---

### Post by 4Orbs on 2009-02-11
Did you see my previous post on Page 1? Did you configure wine first? Don't use two separate drives to install a game, mount the first disc then unmount it and mount the second disc while leaving the game installer open the whole time. It doesn't matter where the iso files are located, just navigate to the necessary folder for either.

---

### Post by AllRadioisDead on 2009-02-11
> **4Orbs said:**
> Did you see my previous post on Page 1? Did you configure wine first? Don't use two separate drives to install a game, mount the first disc then unmount it and mount the second disc while leaving the game installer open the whole time. It doesn't matter where the iso files are located, just navigate to the necessary folder for either.
Yes, I read that. My game is not an iso file, so I can't use gmount. I tried and it spat out this:
```
An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
So I've been trying with a couple of other programs as I mentioned above.

---

### Post by 4Orbs on 2009-02-11
I'll take a look at those programs, but I suspect they work very much like gmount-iso which is just a mount interface for a virtual drive. The important point is to first create a folder for the new mounting place. Then configure wine to see that new folder as the virtual drive.

If you already made it through the first disc portion of the install, I would guess that the folder containing the first disc was established as the mount point. If that is the case, then the second disc should be mounted to the first disc-folder to continue the install. I really don't think that will work because the mount point (folder) should be empty except for whichever file is currently mounted.

---

### Post by AllRadioisDead on 2009-02-11
> **4Orbs said:**
> I'll take a look at those programs, but I suspect they work very much like gmount-iso which is just a mount interface for a virtual drive. The important point is to first create a folder for the new mounting place. Then configure wine to see that new folder as the virtual drive.

If you already made it through the first disc portion of the install, I would guess that the folder containing the first disc was established as the mount point. If that is the case, then the second disc should be mounted to the first disc-folder to continue the install.
furiusisomount is automatically mounting them in my home/username, it's not asking for a mount location, does this mean I should find a different program? I appreciate your help btw.

---

### Post by 4Orbs on 2009-02-11
Are you able to un-mount both images at this time? I'm assuming the game installer is still waiting for the second disc.

---

### Post by AllRadioisDead on 2009-02-11
> **4Orbs said:**
> Are you able to un-mount both images at this time? I'm assuming the game installer is still waiting for the second disc.
I'm unable to unmount the first disc while the installer is running, it claims that the disc is busy.

---

### Post by 4Orbs on 2009-02-11
Can you take a look at the wine configuration "drives" section and see if the /home/yourname folder (drive) has "cdrom" set as "Type" under the advanced settings? But if not, don't change it while the game installer is running.

---

### Post by AllRadioisDead on 2009-02-11
Actually, it does not. I'll try adding it now, and see what happens.

---

### Post by AllRadioisDead on 2009-02-11
Nope, didn't work.

---

### Post by 4Orbs on 2009-02-11
Did you change it while the installer was still running? You probably should have cancelled the installation, then changed the wine config and then started the install over again. I believe wine needs to be closed before the new change is activated.

---

### Post by AllRadioisDead on 2009-02-11
> **4Orbs said:**
> Did you change it while the installer was still running? You probably should have cancelled the installation, then changed the wine config and then started the install over again. I believe wine needs to be closed before the new change is activated.
No, I closed the installation, added the extra drives, and then tried the installer again.

---

### Post by 4Orbs on 2009-02-11
I looked at the furiusisomount site and it appears to have made your /home/yourname folder the mount point, which is fine. When you say you added the drives in wine conf... did you use autodetect (because /home/yourname should have already been listed as a drive) or did you add it manually (without auto detecting) which assigned a second drive letter, when it had already been assigned a letter previously? Regardless the drive letter, you still want wine to install the game on the C drive in your .wine folder.

/home/yourname is the one drive you use for both the .mdf and the .img file. The .mdf should allow unmount so you can mount the .img Maybe changing the furiusisomount type to loop will make a difference.

---

### Post by AllRadioisDead on 2009-02-11
> **4Orbs said:**
> I looked at the furiusisomount site and it appears to have made your /home/yourname folder the mount point, which is fine. When you say you added the drives in wine conf... did you use autodetect (because /home/yourname should have already been listed as a drive) or did you add it manually (without auto detecting) which assigned a second drive letter, when it had already been assigned a letter previously? Regardless the drive letter, you still want wine to install the game on the C drive in your .wine folder.

/home/yourname is the one drive you use for both the .mdf and the .img file. The .mdf should allow unmount so you can mount the .img Maybe changing the furiusisomount type to loop will make a difference.
I added it manually, it just won't let me unmount the first CD during install.

---

### Post by 4Orbs on 2009-02-11
O.K. Lets go back to some initial wine stuff. When you first install wine, before installing anything with wine you need to open its configuration utility. Opening the config automatically creates all the folder structure and C drive in wine. I am thinking that if you didn't open the config first, then wine is installing your game nowhere. If you did not open the wine config as your first step, then I would recommend uninstalling wine and deleting the .wine (hidden) folder in your /home/myname folder. Then reboot and re-install wine, then open the config utility, set your audio source, then use autodetect to view the drives it already recognizes. I would guess that /home/myname will be already there as drive D: so you don't need to add it manually.

Now, if you were trying to install the game BEFORE configuring wine, it just isn't gonna work. So re-installing wine correctly is the way to go.

But if you did install wine correctly, then the problem is with the wine configuration of that drive(/home/myname) or the configuration of furiusisomount (loop or other option). I suspect it is a problem in wine config, because wine won't release the drive for unmounting.

You might want to navigate to inside your .wine folder and see if any game files have actually been created yet. This would verify that the installer is putting them in the right place.

---

### Post by AllRadioisDead on 2009-02-11
I don't think it has anything to do with my wine installation, I've installed plenty of programs with it thus far. I've configured wine to detect the game drives as well. I believe that furiusisomount doesn't release the drive is because the drive is busy running the installer, because I've tried releasing the drive when the installer isn't running it works. None of the game files have been created in my wine folder yet.

---

### Post by 4Orbs on 2009-02-11
Sorry, I misunderstood. I thought that you had just installed wine for the first time for this game specifically. Is this the first virtual drive you have used on wine? If the game installer is prompting you for the second disc then it should release the first for unmounting even though the installer is still running. It's possible that this particular game or furiusisomount are not compatible with the version of wine you have installed. You might ask about this on the wine section of these forums. I'll take a closer look at furius later, maybe install it myself and check it out.

By the way, are you running Ubuntu as a wubi install or a physical hdd installation?

---

### Post by AllRadioisDead on 2009-02-12
> **4Orbs said:**
> Sorry, I misunderstood. I thought that you had just installed wine for the first time for this game specifically. Is this the first virtual drive you have used on wine? If the game installer is prompting you for the second disc then it should release the first for unmounting even though the installer is still running. It's possible that this particular game or furiusisomount are not compatible with the version of wine you have installed. You might ask about this on the wine section of these forums. I'll take a closer look at furius later, maybe install it myself and check it out.

By the way, are you running Ubuntu as a wubi install or a physical hdd installation?
Physical installation, btw the game is SimCity 4000 if you'd like to know, I can show you where I got it if you're interested.

---

### Post by AllRadioisDead on 2009-02-13
Hey guys! After a day of playing with it I finally fixed it. I used AcetoneISO2 to mount the first CD, begin installation, and when it prompted for the second one, I went into wine's drive config tab, and pointed my default CD drive to the location of my virtual drive which was home to the second CD. I managed to finish the installation!

---

### Post by 4Orbs on 2009-02-13
Glad you got it working. Man, I was just getting more and more confused.

---

