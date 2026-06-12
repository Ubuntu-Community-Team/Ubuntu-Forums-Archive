---
title: "How to transfer Home folder?"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by oxf on 2009-06-05
I'm in the process of moving from Hardy to Jaunty. I did NOT create a separate /home partition. Is it OK if I just copy my /home folder or at least select other /home subfolders somewhere else and then reinsert them after its installed? Or are there any problems doing it this way? Essentially what I'm asking is with a new release is are there any changes to the core installed /home folders?

Thanks

---

### Post by Kareeser on 2009-06-05
*Essentially*, no. Your home folder provides configuration options and the like. Heavy-duty config scripts are contained in /etc and are updated by the updater (and prompts you if needed).

Backing up your home folder (try .tar.gz!) and restoring it should not cause any problems.

---

### Post by oxf on 2009-06-05
> **Kareeser said:**
> *Essentially*, no. Your home folder provides configuration options and the like. Heavy-duty config scripts are contained in /etc and are updated by the updater (and prompts you if needed).

Backing up your home folder (try .tar.gz!) and restoring it should not cause any problems.

Can you tell me how to do that, .tar.gz?  I had been thinking about simply copying them over to  a flash drive
Thanks
Mike

---

### Post by braete on 2009-06-05
tar.gz is an archive format.
you just right click, select create archive, and from the dropdown list you chose tar.gz

archive /home to have a backup in case something happens

---

### Post by oxf on 2009-06-05
> **braete said:**
> tar.gz is an archive format.
you just right click, select create archive, and from the dropdown list you chose tar.gz

archive /home to have a backup in case something happens

Thanks :)

---

### Post by eMJayy on 2009-06-05
> **oxf said:**
> Can you tell me how to do that, .tar.gz?  I had been thinking about simply copying them over to  a flash drive
Thanks
Mike

Hi. I take it that what you want to do is backup the folder contents of your home folder? 

tar.gz is the Linux equivalent of a zip file. All you need to do is to open your home folder and select the folders that you want to save (to select multiple folders simultaneously, just hold down the Ctrl button while selecting). Then right click and select ***create archive***. 

You can choose the location where the tar.gz file is saved (i recommend saving it to desktop), as well as choose to archive the files in other formats including .zip. Depending on how much data is in your home folder, it could take some time to archive everything. 

Once the archive is created, you should open it to see that it has everything in you want in it. Then put a copy of it on your pen drive. After installation of your new OS, you can extract the contents of the archive to your new home folder.

---

### Post by greyfox1 on 2009-06-05
I highly recommend taking the time to mount a separate partition to your /home location so you don't have to go through this backup process every time you re-install.  This is what I do and it has saved my butt on more than one occasion. 

If you DO plan on moving your /home folder to a separate partition (even if just for backup) and you don't use the .tar.gz option, be sure NOT to just copy it over in Nautilus as this will mess with folder permissions and cause problems.

This is a handy guide: [http://www.linuxmint.com/wiki/index.php/Move_home_to_its_own_partition](http://www.linuxmint.com/wiki/index.php/Move_home_to_its_own_partition)

It's written for Mint, but there's really nothing Mint-specific about it. HTH

---

### Post by oxf on 2009-06-05
> **greyfox1 said:**
> I highly recommend taking the time to mount a separate partition to your /home location so you don't have to go through this backup process every time you re-install.  This is what I do and it has saved my butt on more than one occasion. 

If you DO plan on moving your /home folder to a separate partition (even if just for backup) and you don't use the .tar.gz option, be sure NOT to just copy it over in Nautilus as this will mess with folder permissions and cause problems.

This is a handy guide: [http://www.linuxmint.com/wiki/index.php/Move_home_to_its_own_partition](http://www.linuxmint.com/wiki/index.php/Move_home_to_its_own_partition)

It's written for Mint, but there's really nothing Mint-specific about it. HTH

Thanks for the guide..just what I need!

---

