---
title: "New to ubutu..need help!"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by cityydude on 2010-03-23
I'm a newbie and know very little about ubuntu. I tried installing it on a new 1TB HDD. It goes fine until it gets to installing the basic system. I get an eror that says "Cannot install basic system". I tried to reinstall it by burning the iso to a new CD at the slowest speed possible on my system (16x) It then began to install the basic system but encountered a new problem. It now tells me that some of the files are corrupted and it cannot continue with the installation fo the basic system, so I'm back to square one again. I know nothing about linix and not much about any other language either so any help thats not too involved would be appreciated. 
 
Thanks

---

### Post by wojox on 2010-03-23
Check the md5sum: [MD5SUM on Windows]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows")

Are you burning on a DVD or CD-ROM?

---

### Post by soluckytouselinux on 2010-03-23
Hi. You can burn a cd or dvd. what you install it with is what you have. if you have a dvd player, you can install ubuntu with a dvd. if you only have a cdrom, then burn ubuntu to a cd. cheers!!

---

### Post by ssulaco on 2010-03-23
> **wojox said:**
> Check the md5sum: [MD5SUM on Windows]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows")

Also,16x speed sounds high.you might try a different iso burner,...Yes,lowest setting.
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)

---

### Post by Mark Phelps on 2010-03-24
If the CD is good, which I suspect it is, then there is a problem with the installer reading and writing using your hard drive.

Suggest you boot from the LiveCD, choose the first mode (try it), do NOT attempt an install, go to the Administration pulldown menu.

Select Partition Editor and confirm that you can see the drive and that the information is correct.

If you get an indication of "no drives", then the installer can not even see your drive.

---

### Post by readycarpenter on 2010-03-24
> **Mark Phelps said:**
> Suggest you boot from the LiveCD, choose the first mode (try it), do NOT attempt an install, go to the Administration pulldown menu.

Select Partition Editor and confirm that you can see the drive and that the information is correct.

If you get an indication of "no drives", then the installer can not even see your drive.

if you see the hard drive in the partition mananger, and you are still having problems with installing, it could be your cd/dvd drive, or the disk was burned with errors, 

when you boot a ubuntu install disk, there is an option to check disk for errors, I'd try that before attempting to install

---

### Post by justanothergreysky on 2010-03-24
You know, it could be a corrupt ISO file as well.  Perhaps the ISO file got corrupted in downloading and no matter how you burn it, it won't work.

This used to happen to me a lot when I was using a wifi with a poor signal as I used to have to do at my old house.  Seems like 1 out of every 6 or 8 big downloads would have trouble like that.

---

