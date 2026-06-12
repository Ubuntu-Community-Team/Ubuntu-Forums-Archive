---
title: "how to retrieve files after installing Ubuntu 11.04"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by ddjamat on 2011-05-23
Help, I installed Ubuntu 11.04 but forgot to backup my documents (pictures). I installed it with a usb stick. I think the drive is formatted. Is it possible to retrieve my precious pictures.
 
 
Dino

---

### Post by Joe of loath on 2011-05-23
Try photorec/testdisk, but you might not get any back.

Cross your fingers and pray :p

---

### Post by Rubi1200 on 2011-05-23
Hi and welcome to the forums ddjamat :-)

Unfortunately, Joe of loath may be right, especially if you have been doing anything with the drive since this happened.

Stop all read/write activities and use the USB stick to boot the computer.

You can then try photorec to get some files back. Be aware that it will not recover the files with the original file-names and you will have a lot of sorting out to do afterwards depending on how much you get back.

Here are some links that can help:
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by Megaptera on 2011-05-23
I'm sorry to read of your accident & I hope you get them back.

---

### Post by wildmanne39 on 2011-05-23
> **ddjamat said:**
> Help, I installed Ubuntu 11.04 but forgot to backup my documents (pictures). I installed it with a usb stick. I think the drive is formatted. Is it possible to retrieve my precious pictures.
 
 
DinoHi, there should have been a option to import documents and such when installing if you did that you should be able to see them in ubuntu.

---

### Post by Mark Phelps on 2011-05-24
If testdisk/photorec doesn't work for you and you're willing to spend money to get your pictures back, I recommend the following:
1) Remove the drive from your PC
2) Using a Windows PC, download and install GetDataBack for NTFS from Runtime Software.  
3) Connect your old drive to the Windows PC
4) Run GetDataBack to look for deleted files and directories. Be patient -- it could take hours to do an in-depth scan.  Best to run this overnight.
5) If it finds your files, you will have to purchase it to do the actual file recovery -- and you will have to recover them to a different disk.

---

### Post by garycahill on 2011-05-24
All the best with it. 

Backups are always the best plan :(

---

### Post by Joe of loath on 2011-05-24
> **Mark Phelps said:**
> If testdisk/photorec doesn't work for you and you're willing to spend money to get your pictures back, I recommend the following:
1) Remove the drive from your PC
2) Using a Windows PC, download and install GetDataBack for NTFS from Runtime Software.  
3) Connect your old drive to the Windows PC
4) Run GetDataBack to look for deleted files and directories. Be patient -- it could take hours to do an in-depth scan.  Best to run this overnight.
5) If it finds your files, you will have to purchase it to do the actual file recovery -- and you will have to recover them to a different disk.

Won't work if the partition has been reformatted to a different format AFAIK. Also, Recuva does the same job but for free I believe.

---

