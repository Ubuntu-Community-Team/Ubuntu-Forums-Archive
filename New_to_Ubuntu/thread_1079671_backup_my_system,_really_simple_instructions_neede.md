---
title: "backup my system, really simple instructions needed"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by capnthommo on 2009-02-24
hi everybody,  i have now got an external HDD which i have formatted to Ext3 file system.  it has no (one) partition of about 600Gig.  i want to make a copy of my whole system in such a way that if for example, the present machine got fried (dropped in the bath, kicked down stairs, shot) i could restore it all.  i have no problem with data as i can go gksudo nautilus with the Ext HDD mounted and copy/paste etc.  i know this works 'cos i have already tried it.
i have tried sbackup with no success at all.  what can i use and - in REALLY simple terms cos honestly i don't understand it - how do i make this copy, and restore from it?
i don't mind if i have to install from live cd first but i need to be able to add the apps i have installed and settings changes i have made.
i have looked at the how tos and links that have been suggested in other posts (both mine and other peoples) but really, really can't get myhead round the instructions.
help is all i can say.

---

### Post by ikisham on 2009-02-24
Hi mate, I've never done that and maybe some wiser guy gives you another advice, but you may check this backup tool:
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by Therion on 2009-02-24
**Easy-Peasy Lemon-Squeezy Guide** (using QuickStart and LOTS of screenshots): 

[http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop](http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop)

---

### Post by kestrel1 on 2009-02-24
I don't think remastersys will do what you want. I would suggest a drive imaging program such as partimage: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
You can install it with ```
sudo apt-get install partimage
```
This will take a snapshot of your system & can be restored if it all goes wrong.

---

### Post by capnthommo on 2009-02-24
hi everybody, thanks for your replies.  i have given all these methods another serious go.  not very successful.  the nearest i got was remastrsys to go through the process and then deliver an error message saying the file was too big for the standard and i would have to remove some data.  
so what i got was as follows:
     1.  quickstart won't even install on my machine (and yes i checked the procedure i went through)
     2.  remastersys doesn't want to do it in one piece, only on more than one.  just cant work out that one.
     3.  partimage, again, i couldn't make it do anything - perhaps i need a gui for this cos the cli method is beyond me even following the helps.

so any other suggestions would be appreciated.  i am sorry but i need this to be really simple.  i don't care what happens as long as i get an image/copy/backup/mirror that i can put on my extHDD even if i have to copy it there.
why am i finding this one so difficult, i've spent ages on it and i don't seem to be any further forward.
perhaps some way of just saving the changes from the live cd so i can reinstall that and then run the backup as an update or somthing?
i just feel very unprotected with no backup.
cheers
nigel

---

### Post by MrKlean on 2009-02-25
Well, my two cents LOL! Use remastersys..edit it so you use the external drive as the working folder...run the clean option before you make the change to get rid of extra files. It should do what you want.  It will make a custom.iso file which you can burn to disk and use like the live cd for ubuntu.  If that's not clear enough, I'll try harder to give explicit instructions ; )

---

### Post by Jingle on 2009-02-25
Can't you do a direct copy of the drive with the "dd" command?

---

### Post by bolucpap on 2009-02-25
One very simple way is to boot from a live CD, then mount both the internal and the external harddisks using the places tab on the main menu, and then copy the files from the internal drive to the external drive using nautilus. It may not give you a bootable image, but it will effectively put all your data in a safe place. For a bootable image, I boot from a live cd and dump the original partition to a file in the external harddisk, like so (keep in mind that paths vary from system to system, you should modify the code below to match yours):

```
sudo dd if=/dev/sda1 of=/media/ExternalHDD/Backups/BackupImg.bin
```

Lately, if I am not pressed for time, I've been compressing the image like so:

```
sudo dd if=/dev/sda1 | gzip -9 -f - |dd of=/media/ExternalHDD/Backups/BackupImg.bin.gz
```

Restoring is simple, but will overwrite all new data created since the image was taken:

```
sudo dd if=/media/ExternalHDD/Backups/BackupImg.bin of=/dev/sda1
```
for uncompressed, and:
```
gzip -d -c /media/ExternalHDD/Backups/BackupImg.bin.gz|sudo dd of=/dev/sda1
```
for compressed.

But I strongly suggest reading the documentation for the dd command and basic info on streams and pipe redirection before you try something you do not fully understand.

---

### Post by Michael.Godawski on 2009-02-25
hi,

did you have a look at the community documentation? Perhaps you will find something suitable there..


[LIST]
[*][https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[/LIST]

---

### Post by capnthommo on 2009-02-25
hi again.  first thanks to everybody again for the helps.
okay i have managed to find the quickstart that i thought wasn't installing - it was lurking somewhere on my file system.  i have now used it to successfully create tar files of / /home mbr etc and they occupy about 7Gig (the right amount) of my ext HDD so i think that's okay for now as long as it will restore my system if it should be needed.

bolucpap and jingle,  i shall do some more research on the dd option - it looks pretty simple and if it creates a bootable image on my HDD then that's what i want.  it may wipe out any unbacked up changes, but then isn't that the case with all backups?  but as long as i can just get back to more or less where i was when the backup was taken, if my machine should get fried.  you know what i mean?  if i should maybe have to get a new processor fitted and lose all the current install - restore from nothing?
but unless you are prepared to make a new backup every 5 minutes then there are always likely to be some losses aren't there?

edit)  michael. yes i already have that page bookmarked, i have read it before - thanks

anyway, i now have a backup on quickstart so i can go ahead with the thing that has been making me fret most, and that's to create a separate /home partition - what's been stopping me has been not being able to save a copy of what i have already done.
thanks again, i shall read up on the dd option and check out rsync again.  if i have any more q.s i shall repost.  i think we can mark this solved, at least for now.
cheers again
nigel

---

### Post by robert shearer on 2009-02-25
Remastersys has worked very well for me. I have used it several times on both Hardy and Intrepid.

The thing to bear in mind is that it makes a live cd of your installed and **configured system ** and is not designed to be a **data** backup.

The live cd it makes will allow you to quickly bring back your personalised system and all the updates and installed apps that you've added since first installing.

this quote from the remastersys site should be followed to ensure that the cd/dvd image it makes is not **too large**

> The key is to make sure your /home/(your_username) does not contain a lot of large files, such as MP-3s, videos, pictures, etc.
Move all such files to a separate data partition, and you will find that your system easily compresses to a file size of less than 4 gigabytes. Mine generally is just a bit over 1 gig.
Before Remastering your system, be sure to unmount any other partitions, except for your / and /home, unmount any mounted network drives, and unplug any USB thumb-drives or hard drives, otherwise, Remastersys will include those in the backup, making the ISO file too large.

Also look for the following folder: /var/cache/apt/archives. That folder is where Klikit, (and presumably Ubuntu and other Ubuntu-based distros}, store the DEB files for all the programs installed on your system. The DEB files are binary installers, and once the program is installed, they are no longer needed, unless you need to reinstall the program for some reason. You can copy the entire folder to your storage partition, or use AptonCD to make a backup disk, then you can safely delete the contents of the original folder ( do a "sudo apt-get clean") , which can free up a half a Gigabyte or more.

I also use aptoncd to back-up my added applications and system updates just in case. 
Remember to run and make the aptoncd iso **before** you do a "sudo apt-get clean" as it will remove all those packages from the apt archive.

Hope that helps.
 Remastersys is a really lovely app when used properly and has never once failed me. 
I now use the Debian version to make live install cds of my Debian Lenny system.

---

### Post by kestrel1 on 2009-02-25
If you want to make a seperate /home partition (very good idea) try this link: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

