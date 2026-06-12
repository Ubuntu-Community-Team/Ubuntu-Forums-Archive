---
title: "Transfering files between Windows &amp; Ubuntu"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by magicmax0 on 2009-04-28
Im currently dual booting Vista Ultimate 64bit and Ubuntu 9.04 i386 desktop. They are both installed on the same drive (seperate partitions). I was wondering how i could transfer files from the two, i was thinking maybe creating a new partition and using that in both OS's... if thats possible. What suggestions do you guys have to get it done?

---

### Post by ninjapirate89 on 2009-04-28
Ubuntu should be able to mount the partition that has Vista installed on it so you can browse the files. I know it works for me on my dual-boot with XP.

---

### Post by Saint_ on 2009-04-28
Yeah, while on Ubuntu I can browse/copy/paste/etc. the windows 7 partition, but while in windows I can't view the Ubuntu partition, I'm not sure if it's because i dont have something set up right or as many state "windows believes its the only operating system ever". So hopefully that'll grant a bit of insight.

---

### Post by ninjapirate89 on 2009-04-28
> **Saint_ said:**
> Yeah, while on Ubuntu I can browse/copy/paste/etc. the windows 7 partition, but while in windows I can't view the Ubuntu partition, I'm not sure if it's because i dont have something set up right or as many state "windows believes its the only operating system ever". So hopefully that'll grant a bit of insight.

Oh okay. Yeah windows can't normally read from an ext3 or 4 partition. I think there is a way to make it use ext3 but if you're using 4 you will have to create another partition. I saw a thread about using ext3 in Windows recently. I'll see if I can did it up for ya.

Edit -> Not the thread I saw but this should be what you are looking for (unless you are using ext4).
[http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html]("http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html")

---

### Post by Puz on 2009-04-28
My Windows files are located at /media/disk/. So what I did was open file browser and navigated to there then bookmarked in the filebrower menu Now it shows up in places and I can either add files to there or any subdirectory or drag and drop or cut and paste  between two locations.

---

### Post by ninjapirate89 on 2009-04-28
> **Puz said:**
> My Windows files are located at /media/disk/. So what I did was open file browser and navigated to there then bookmarked in the filebrower menu Now it shows up in places and I can either add files to there or any subdirectory or drag and drop or cut and paste  between two locations.

The OP needs to access his (her?) ubuntu file system from Windows though.

---

### Post by magicmax0 on 2009-04-28
I was also thinking of getting a 2nd HDD, I was planning to use this to store all my media files. If i formated this HDD from windows, would Ubuntu be able to mount that as well?

---

### Post by ninjapirate89 on 2009-04-28
> **magicmax0 said:**
> I was also thinking of getting a 2nd HDD, I was planning to use this to store all my media files. If i formated this HDD from windows, would Ubuntu be able to mount that as well?

If you want to be able to access a second hard drive from both Windows and Ubuntu, you should probably format it as NTFS or Fat32. I use an external hard drive to store all of my media files. By default it is formatted as Fat32 (I think) so I can access it from both.

---

### Post by magicmax0 on 2009-04-28
> **ninjapirate89 said:**
> If you want to be able to access a second hard drive from both Windows and Ubuntu, you should probably format it as NTFS or Fat32. I use an external hard drive to store all of my media files. By default it is formatted as Fat32 (I think) so I can access it from both.

Thanks for the info. Basically, my plan is to be able to upload all of my torrent media files while being in either operating system, if thats possible. Often times I prefer to be on Ubuntu when doing my daily things, I just need windows for certain software and games. However, I cant upload my files while im on Ubuntu right now. It would also be nice to be able to download files in either OS to a shared drive(or partition). I figured maybe a 2nd HDD would make this easyer.

---

### Post by cariboo on 2009-04-28
If you formatted the linux partition as ext3 you can use [this]("http:///www.fs-driver.org/download.html") driver.

If you formatted the partition as ext4 you are out of luck, as the windows guys haven't updated their software

---

### Post by ninjapirate89 on 2009-04-28
> **magicmax0 said:**
> Thanks for the info. Basically, my plan is to be able to upload all of my torrent media files while being in either operating system, if thats possible.

That should be easily done, although I don't use upload torrents so I'm not certain. In theory it will work.

---

