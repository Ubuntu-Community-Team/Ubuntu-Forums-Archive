---
title: "Help With Dual Boot ????"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by dinomite89 on 2009-01-01
Hey All,

Ive tried setting up a dual boot of hardy heron and vista, after installing hardy heron i have received GRUB 17 Error and after some digging around i came to a Super Grub Disc witch i used as best i could (i am a very big n00b at this) and now i can get to Ubuntu through the disc but cannot boot to windows, my boot mgr is missing, also my vista install disc is at my other house and i have no access to it, are they're other boot managers around the could boot vista for me or can i re-install grub, any help would be great

---

### Post by award982 on 2009-01-01
okay dude,do this. get a freedos install disk,and go through the few steps til you come to the boot manager.set up the boot manager to only boot windows,and restart pc.
then use the disk u mentioned before to boot ubuntu,and use the bootloader to boot to windows :P

---

### Post by bumanie on 2009-01-01
To fix the vista boot loader go to [here and download]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") the repair disc. After you have repaired the vista boot loader, follow [this]("http://ubuntuforums.org/showthread.php?t=224351") to reinstall grub. Then your computer should boot fine again.

---

### Post by award982 on 2009-01-01
oh,and also make sure u really delete the other bootloader,simply at menu select an option to install the bootloader,couse if u dont install it after u set it up,ull have to do it all over again (lol,when i was a beginner that was my mistake:P)

---

### Post by award982 on 2009-01-01
> **bumanie said:**
> To fix the vista boot loader go to [here and download]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") the repair disc. After you have repaired the vista boot loader, follow [this]("http://ubuntuforums.org/showthread.php?t=224351") to reinstall grub. Then your computer should boot fine again.
 
 
dont listen to him:o

---

### Post by dinomite89 on 2009-01-01
I Tired that and i got no differnce, unless i fail bad will rty other option sounds better as vista is more important atm.

---

### Post by mkvnmtr on 2009-01-01
Think about who you wish to take advise from. A person with over 2600 post and many people who have thanked him or someone with 3 posts who has never been thanked by another user.

---

### Post by dinomite89 on 2009-01-01
Too True never thaught of that, will keep in mind, i am in dire staights atm, i need my vista back, so first sultion got first trial lol

---

### Post by caljohnsmith on 2009-01-01
Often a "BOOTMGR missing" error is not a problem with Vista being broken, but simply a problem with booting the wrong partition; if you try and boot a data NTFS partition that was created by Vista, you will get a "BOOTMGR missing" error. So in order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by dinomite89 on 2009-01-01
Ok thanks i got ym vista back and can still use Linux although im still having to boot off my super grub disc, when i try to boot Linux normally it tells me it cannot mount the partition, i tried the steps for reinstalling the grub from the live CD, any ideas?

---

### Post by award982 on 2009-01-02
> **mkvnmtr said:**
> Think about who you wish to take advise from. A person with over 2600 post and many people who have thanked him or someone with 3 posts who has never been thanked by another user.
 
sure,that i just registered that matters the most,but that i am an experienced developer and programer that doesnt count right?

---

### Post by award982 on 2009-01-05
> **dinomite89 said:**
> Hey All,

Ive tried setting up a dual boot of hardy heron and vista, after installing hardy heron i have received GRUB 17 Error and after some digging around i came to a Super Grub Disc witch i used as best i could (i am a very big n00b at this) and now i can get to Ubuntu through the disc but cannot boot to windows, my boot mgr is missing, also my vista install disc is at my other house and i have no access to it, are they're other boot managers around the could boot vista for me or can i re-install grub, any help would be great

1.FIRST INSTALL WINDOWS!!!!!!!
2.ONLY THEN INSTALL LINUX (hardi heron is old,get the newest install disk,8.10)

---

