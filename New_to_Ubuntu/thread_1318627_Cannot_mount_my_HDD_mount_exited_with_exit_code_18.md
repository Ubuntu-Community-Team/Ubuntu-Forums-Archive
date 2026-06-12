---
title: "Cannot mount my HDD mount exited with exit code 18"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by LanceyD on 2009-11-07
I'm trying to mount a 2nd HDD and I get this error

[I]"Error mounting: mount exited with exit code 18: Failed to open hiberfil.sys data attribute: No such file or directory
Failed to mount '/dev/sdb3': No such file or directory"[/I]

It is specific to this particular HDD that has Windows Vista installed.  I can mount other HDDs with the same installation.  I just don't understand the error code.

---

### Post by twisted_steel on 2009-11-07
While not the same error message, it appears that it could be related to hibernation.  Did you hibernate Vista the last time you used it?  Did you encounter this by mounting the drive from within the GUI or via command line?

There is an option in ntfs3g [1] that will remove this hibernation file if that is indeed the problem.  Keep in mind that you will not be able to resume Vista next time you boot up.

Keep in mind that 'location' is just a placeholder for wherever you normally mount drives (e.g. in /media/...).

```
sudo ntfs-3g /dev/sdb3 /mnt/location -o remove_hiberfile
```[1] [http://fedoraforum.org/forum/showthread.php?t=180116](http://fedoraforum.org/forum/showthread.php?t=180116)

---

### Post by LanceyD on 2009-11-08
thanks twisted_steel.  

I have read the link you provided also.   I understand the problem now.  This is one of 4 HDDs removed from identical machines when they were returned to DELL so there is no need for them to ever reboot windows, but i need to access the files for transfer.  The other 3 I have accessed fine, this one may have been on hibernate when the HDD was removed then.  (I have a feeling i did access this one previously one an XP setup...)

I get this error now after running the terminal command

> Failed to open hiberfil.sys data attribute: No such file or directoryAnd the same error when trying to mount through File Browser 
> **Unable to mount OS**
Error mounting: mount exited with exit code 18: Failed to open hiberfil.sys data attribute: No such file or directory
Failed to mount '/dev/sdb3': No such file or directoryIncidentally there are two other partitions on this HDD "DellUtility" and "RECOVERY" which i have mounted with no problems.

I'm guessing there is another file on the HDD pointing it to the hiberfil.sys, but this file doesn't exist.  Maybe i need to ask on another forum.

---

### Post by twisted_steel on 2009-11-08
There is a forum and mailing list for NTFS-3G under Support on this page:

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

It could just be that your drive is in some weird state that the software isn't expecting.  Be sure to post back here if you find anything.  This is one of the few results on Google ;)

---

### Post by LanceyD on 2009-11-09
I've posted the question there and i await an answer.

I have accessed the dive in read only format using SLAX live CD boot.  I'm not sure what handler SLAX uses for mounting drives (it's an old version) anyone know?  I'll install that instead to sort this drive out.  Cheers.

---

