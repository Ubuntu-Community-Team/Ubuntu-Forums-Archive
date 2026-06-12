---
title: "Need help in backing"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by berri67 on 2009-11-16
up to USB Drive.  I tried using the program that comes with
Ubuntu 8.04 LTS and it says something like this:

  It is recommended that you verify the integrity of the newly
  created backup archive, would you like to proceed with the
  verification.  Make sure that the first medium of the newly
  created backup archive is accesible or located in drive.

  The medium does not seem to contain valid hu backup data.  Please
  make sure medium #1 backup set is in drive and retry.  (you can always use the verify button independently.

Then it goes through backing up but when it goes to verify, it does not verify and the backup doesn't work cause the stuff from the folders are not on the USB.

Is there any other way by terminal command to back up to the USB drive?

Thanks for any help.
:)

---

### Post by HalfEmptyHero on 2009-11-16
I don't really back up my stuff, but if you tell me which folders you want to back up it wouldn't be too hard to write a python script to do it.

---

### Post by berri67 on 2009-11-17
> **HalfEmptyHero said:**
> I don't really back up my stuff, but if you tell me which folders you want to back up it wouldn't be too hard to write a python script to do it.

I want to back up my home file which is berri and also the file system folder.

:)

Thanks.

---

### Post by HalfEmptyHero on 2009-11-17
Here is a very simple bash script that will backup your root filesystem as well as your home folder. It is just the following two lines

```

sudo cp -uvr / /media/disk/backup/root/
cp -uvr ~/ /media/disk/backup/home/

```

Make sure you change the location from /media/... to the location of your external hard drive and where you want it to be backed up.

Basically it copies all files onto your hard drive only if the files on your computer are newer than the ones on your hard drive. It will not delete anything on your hard drive, so if you uninstall programs or delete files on your computer they will still be on your hard drive. 

You may need to do chmod +x backuphd.sh first, and if you want to be able to backup your hard drive just by typing in backuphd, rename it to backuphd (remove .sh) and copy it to /usr/bin/ (sudo cp backuphd /usr/bin/). That way anytime you type in backuphd it will run the script.

Hope this helps, sorry it can't do any more.

---

### Post by updog on 2009-12-17
I recently downloaded [http://simplebashbu.sourceforge.net/](http://simplebashbu.sourceforge.net/) and tweaked it to suit my needs successfully. However I am looking for the correct way to exclude sub directories in the backup paths.  For example, I would like to back up all of /home with the exception of a couple larger directories in /home/samba/public/ that hold one of my user's massive music collection. any advice would be much appreciated.

cheers,

sean

---

### Post by garyed on 2009-12-17
```
 
rsync -avhu --exclude samba/public/  /home /backup

```

will copy everything in the home directory & below except the public directory to /backup.
You can exclude others just by adding another --exclude option:
```
 
rsync -avhu --exclude samba/public/ --exclude people/  /home /backup

```

I think rsync is a better command for backups in general.  
You might need sudo depending on permissions.

---

### Post by updog on 2009-12-18
awesome, thanks for the help Gary.

---

