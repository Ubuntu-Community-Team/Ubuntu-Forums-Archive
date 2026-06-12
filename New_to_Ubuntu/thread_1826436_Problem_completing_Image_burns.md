---
title: "Problem completing Image burns"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by avnd on 2011-08-16
Hello!

I've tried burning .iso images in 3 programs.

1. ImgBurn in Windows 7
2. Brasero in Ubuntu 11.04
3. K3b in Ubuntu 11.04

In all 3 programs, the image burning part goes fine (which I assume because the progress bar and the captions underneath go through that part with no hitches). 

The part that follows (synchronizing cache, finalizing, etc.. the term varies with each program I believe) just does not complete. The PC hangs at that stage for 15 to 30 minutes and then gives up saying the process was a failure. 

The .iso files that I burn (and were 'aborted') actually boot fine. The data files (like documents and music) don't appear to burn and when I load those discs, the PC says that the disc is empty (although I saw the progress bar showing data written during the process and the lines I can see on the surface of the disc). 

I initially had this problem with ImgBurn and Brasero and some threads suggested that K3b was much better. I then tried K3b. I tried burning 2 .iso's.

1. In the 1st disc, I'm not sure if I selected multisession and the rest of the settings were pretty much default. The data burned in about 5-7 minutes and it 'hung' (drive light still blinking all the time) for about 15 more minutes. It eventually completed though.

2. In the 2nd disc, I selected multisession and it hung. The process eventually failed.

I'm not sure if selecting 'multisession' was relevant but that's about the only difference I can remember. I checked the md5sums of both the images. They were fine.

I don't have logs of the ImgBurn and Brasero events. But I save the output of the 2 K3b events. I've attached them. 

Any help is greatly appreciated.

Thanks.

---

### Post by corncob on 2011-08-16
I might be behind the times but I thought if you chose 'multisession' the disk would wait for you to add another session and wouldn't run until you closed it.  Anyway, I wouldn't have selected that option.  Always thinking hardware -- do you have another burner you could try?  
A friend wasn't able to burn CDs and, by way of trouble shooting, I took the drive out of her computer, put it in mine, and it worked.  Put it back in her's and it didn't.  Never did figure it out but she bought an external USB drive and that worked.

---

### Post by avnd on 2011-08-21
Thanks for the reply, corncob.

---

