---
title: "Urgent, Disaster with fsck"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by mikesol on 2009-09-29
Hello I have I little big problem with Ubuntu,

I had to reinstall it and I have /home in other partition, and then for some reason the system asks me run fsck for repair "something".

I agree and then I discovered that all my files had been moved to a folder lost+found, with a sequence of strange numbers.

```

    #10174630  #5578777  #5578993  #5579077  #5580874  #5595866  #6694586  #6695089  #7831964  #7880772  #8011791  #8184119  #8519723  #8642574  #9732177 #10174637  #5578778  #5578998  #5579083  #5580875  #5603466  #6694587  #6695090  #7831980  #7888974  #8028161  #8184157  #8527873   

```


So anyone knows how can I recover my files with his names in my home directory?

Thanks a lot for all your help.

---

### Post by Zeedok on 2009-09-30
I'm no expert, but if your system is asking you to run fsck that may mean there are bad sectors on your hard drive. 

I would copy all of your files of your drive as soon as possible (put them onto a flash drive or external hard drive) then check the drive with fsck.  If you are dual booting with windows and have an NTFS partition, then run chkdsk (I think that's what it's called) in windows to check for errors there.  Once the disk has been checked copy the files back into your home partition -- but be prepared in case there are more disc problems (ie BACK-UP!!!)

PS - for all the copying and backups, can I suggest rsync, or if you want a GUI which simplifies things, try Grsync. They are both in the repositories.

---

