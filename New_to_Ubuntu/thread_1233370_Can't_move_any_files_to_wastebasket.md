---
title: "Can't move any files to wastebasket"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by clarett on 2009-08-06
Hi

I'm super new to all this - only 1 week with ubuntu and I seem to have lost the function of the wastebasket.
I have 2 hard drives - one external which was formatted in windows and the other which is extJ3.  Thing is it was working but now I can't delete things to wastebasket from either hard drive.  I get this message "Cannot delete this to wastebasket, do you want to delete immediately?"

I have looked for a solution but have found the answers start with a level of knowledge I don't have yet.

Can anyone help out?
Oh I'm using hardy 8.04.03

Thanks

---

### Post by Sidewinder1 on 2009-08-06
First.*** Welcome*** to Ubuntu forums!
I must say I've never seen this question before. Were you doing anything out of the ordinary recently, before this happened?

---

### Post by clarett on 2009-08-07
I had been trying to get the flash player to work in opera which took 3 evenings of fiddling to get!!
I uninstalled, reinstalled flash, deleted a link using terminal from this folder - usr/lib/mozilla/plugins  and tried adding the command line that they have in the documentation section for troubleshooting flash.  
The folder for the wastebasket is still there - I checked that but didn't know what else to do.
I've seen quite a few posts about the wastebasket not working for NFTS formatted drives but none for it not working with the home file system.

Any ideas??

---

### Post by pmlxuser on 2009-08-07
check in the NTFS drive for a folder (hidden) -so setting should say view hidden folders its usually named .trash

ie if the drive is media0 then it would be in /media/media0/.trash

---

### Post by super kim on 2009-08-07
i have an 8gb hdd (sda1) ext4, that has ubuntu (karmic) and nothing else on it. a 160gb hdd (sdb1) fuseblk that has just media files on it. and a 360gb hdd (sdc1) ext3 which has ubuntu (jaunty) and some media files.

the deleted items folder works for both the 8gb and hte 160gb drives but not for the 360gb hdd. i assume this is due to user privelages 
here is an example of a file i have saved on all three drives and tried to send them to the deleted items folder...
[http://img13.imageshack.us/img13/6381/screenshot1cdy.png](http://img13.imageshack.us/img13/6381/screenshot1cdy.png)
[http://img148.imageshack.us/img148/6607/screenshot2cct.png](http://img148.imageshack.us/img148/6607/screenshot2cct.png)

---

### Post by furuno on 2009-08-07
Are you intalling Ubuntu under Windows? If that so, from my experience, you cannot delete item from another partition to the trash can, instead you have to delete them permananently. 

I know there's should be some way to do this but I just don't know about this...

---

### Post by clarett on 2009-08-08
pmlxuser - there's no trash folder from linux though I seem to have found 2 from windows!! (I know they're from windows cos there's a film in there that I watched and deleted ages ago)

furuno - no.  I reformatted the disc and installed linux - the drive I had been using as storage before so it hasn't had an operating system on it for at least a year before now.

What I find weird is that it did work for a while.....

---

