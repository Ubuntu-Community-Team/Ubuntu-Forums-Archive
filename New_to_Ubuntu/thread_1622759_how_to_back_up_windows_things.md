---
title: "how to back up windows things"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by maclover on 2010-11-15
ok so i backed-up or think i did my linux stuff (programs files) using Déjà Dup and it given me PGP/MIME files since i wanted it encrypted but was that a good idea and how do i open them? and i would also like to know how to back up all of my windows programs files all the stuff using ubuntu since when i go on windows it gives me a ton of error boxes and the normal windows things. sorry if it didnt make a ton of scene to you since its late where i am at and ive been trying to figer this out for some time now:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by ironic.demise on 2010-11-16
> **maclover said:**
> ok so i backed-up or think i did my linux stuff (programs files) using Déjà Dup and it given me PGP/MIME files since i wanted it encrypted but was that a good idea and how do i open them? and i would also like to know how to back up all of my windows programs files all the stuff using ubuntu since when i go on windows it gives me a ton of error boxes and the normal windows things. sorry if it didnt make a ton of scene to you since its late where i am at and ive been trying to figer this out for some time now:confused::confused::confused::confused::confused::confused::confused::confused:
 I don't deal with DejaDup, I'm an old fashioned backup man.
Encryption *should* be fine, Either it uses an encryption that is standard (i.e. *Blowfish*) or you will be able to access and unencrypt the file using DejaDup itself.
 
On Ubuntu you should be able to access your Windows partition or harddrive from the "places" menu near "Applications" on the top panel, in there if you want to backup *everything* just copy it all into your Ubuntu partition if you **just** want your documents then copy "***your_wind_partition***/Documents and settings/your_username" (assuming WinXP)

---

### Post by Mark Phelps on 2010-11-16
IF your goal is to do a Windows backup from which you can later restore programs, as well as data, using any file backup utility (Windows or Linux) will NOT do that -- regardless of what you're being told by others.

Windows programs depend critically on entries in the Windows registry -- which will NOT get backed up if you only back off certain folders.

Your best best is one of the following:
1) Use Clonezille, in Ubuntu, to image off your Windows partition to another drive or an external drive.  That will save everything in that partition and can be used later to restore the same partition if needed.
2) Use Macrium Reflect, in Windows, to image off your Windows partition ...  You can go to their website, download and install their free version, and also burn a restore CD using that version.

---

### Post by maclover on 2010-11-17
> **Mark Phelps said:**
> IF your goal is to do a Windows backup from which you can later restore programs, as well as data, using any file backup utility (Windows or Linux) will NOT do that -- regardless of what you're being told by others.

Windows programs depend critically on entries in the Windows registry -- which will NOT get backed up if you only back off certain folders.

Your best best is one of the following:
1) Use Clonezille, in Ubuntu, to image off your Windows partition to another drive or an external drive.  That will save everything in that partition and can be used later to restore the same partition if needed.
2) Use Macrium Reflect, in Windows, to image off your Windows partition ...  You can go to their website, download and install their free version, and also burn a restore CD using that version.

ok mark thnxs all i really wanted to do is to back every thing up on my windows side and yes it is winxp but i was able to back everything up using my xp side and ill use that other program that(sorry but forgot your name) the first post reply was...but should i del the files that i back up using that program and do a fresh back up?

---

### Post by ironic.demise on 2010-11-18
If you do an image, there's no need for photorec or foremost.
If you want programs, users and settings backed up then make an image, if you ONLY want files, use photorec or just copy+paste (photorec is for deleted files really...)

---

### Post by Mark Phelps on 2010-11-18
Unless backup space is at a premium, it's generally a lot faster and easier to back up entire partitions.  You don't have to find all the files and you don't have to worry about missing any.

IF you're just backing up files, you don't really need an app to do that.  Just connect an external drive, open it in Places, and use a file manager to copy the files over to the external drive.

---

