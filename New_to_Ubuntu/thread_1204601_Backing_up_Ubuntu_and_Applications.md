---
title: "Backing up Ubuntu and Applications"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by nomes on 2009-07-04
Hi, so I have finally made a switch to Ubuntu 64 bit Jaunty and dont have any other OSs around.  For the past week I have been lurking around this forum trying to get everything working and now I would like to back up my system so that if there is a hardware failure or OS failure ill have something to restore.  All my personal data is backed up two or three times.  

So the my questions  as a stranger to Ubuntu are: how to i go about backing up and restoring just the OS itself and  Applications on my system?  Can it be done within Gnome or KDE or is it extensive console typing? Can it also be  automated to be done periodically? What do experts or more advanced users do to back up their systems?

Thanks

---

### Post by diablo75 on 2009-07-05
Well to do it manually, go to Places>Home Folder and press CTRL-H to reveal all hidden files (those that begin with a .period).

Then just copy/paste all files to your backup media.  You could also right click and create a tar.gz/zip file archive of all of this stuff.  There's even an option to create multiple tar.gz's at a specific size (e.g., 1 GB per file) if you need to move the data to something like a DVD.

In the event of a crash, you could just format the hard drive, reinstall Ubuntu using the same username as your current account, and then paste your backup copies back into your home folder.  This will restore all your previous application settings.  It won't reinstall your software for you, but getting software reinstalled in Ubuntu is a snap using either the Applications>Add/Remove applet, or System>Administration>Synaptic Package manager, or even the sudo apt-get install (application names spaced apart) in the terminal.

There are automated softwares out there you could try.  I'd check the Add/Remove applet I mentioned to see if the search for "backup" turns anything up.  I'm lazy and haven't checked anything out but I'm sure there's something worth while in there.

---

### Post by diablo75 on 2009-07-05
One other suggestion... something to try when you're feeling up for it.

To make this whole backup/restore process faster, try installing Ubuntu using the manual partitioning.

Say you start with an empty drive.  Start by creating the first partition at about 10 GB in size or so (maybe a little more if you intend to install a lot of applications).  Then make sure this partition's mount point is set to be / (the root partition).

Next, create another partition after this first one filling up almost the rest of the hard drive (leave 2x the amount of RAMs worth in your system for the final swap partition).  Set the mount point for this second partition to /home.  This partition will now house your home folder, seperate from the first partition.

The last partition will be the swap.

Now, in the event of a horrible crash or use error....  Just delete the first partition, reinstall using manaul partitioning, and tell it to NOT format the second partition and go ahead and use it as the /home.  If you install using the same user name you did last time, everything will be as you left it.  Application settings, user preferences, it'll already be restored.  Saves you a bunch of time.

---

### Post by LewRockwell on 2009-07-05
Honestly, with used-but-still-good hard drives being very easy to find and inexpensive/free and something like this([http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062))

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

Whole drive cloning via something like Clonezilla or Parted Magic(has Clonezilla along with other great utilities) is the MOST fool-proof method...

And isn't your peace-of-mind worth it!?!

Oh, and Parted Magic has an "Erase Disk" utility that engages the hard drive's internal(board level) secure erase function...neat!
(search "secure erase" for more on this "secret" hard drive function)

Here are a few links for your reference:
(note that you DO NOT need a separate device to use secure erase feature of your hard drive!)

[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

[http://www.wiebetech.com/products/Drive_eRazer.php](http://www.wiebetech.com/products/Drive_eRazer.php)

[http://www.semshred.com/contentmgr/showdetails.php/id/1191](http://www.semshred.com/contentmgr/showdetails.php/id/1191)

[http://www.machine-solution.com/products.asp?dept=241](http://www.machine-solution.com/products.asp?dept=241)

Get 'em and Use 'em!

And...as always, your mileage may vary, buyer be aware and beware...

.

---

### Post by nomes on 2009-07-06
thanks a lot to your replies...there  are definitely many choices here to backup and restore now the hard part is choosing which one....is best suited for my purposes.....

---

### Post by theozzlives on 2009-07-06
[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

