---
title: "Change from Wubi to normal installation?"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by mabynke on 2010-08-17
Hello, Ubuntu people!
Maybe a couple of months ago, I wanted to try using Ubuntu, and installed Ubuntu 10.04 on my laptop using wubi. But now, I want to use it as my main OS. And now to my main question: Can I continue to use the current installation, so that I can keep my files and programs, and in some way make it independent of Windows? (I don't know exactly how wubi works, but I am guessing that it makes a partition as needed and installs Ubuntu the regular way, except adding an uninstallation program in Windows. Am I right?)
And if I remove Windows, or it stops working, will my Ubuntu installation still be functional?

And another thing - I read [this thread]("http://ubuntuforums.org/showthread.php?t=1543785") and found out that you can easily take disk space from Windows and give it to Ubuntu. Is this the case also with a wubi installation? Wubi wouldn't let me give Ubuntu more than 8 GB of disk space, which of course isn't enough.

Thanks in advance for replying! :)

And another little question: People are talking about Linux swap partitions. What are these? Do they correspond to Windows FAT partitions?

---

### Post by GaryTheCat on 2010-08-17
Possibly a silly question - but I thought I'd installed Ubuntu as a wubi install but it turned out I haven't.

Did you click "Install inside windows" when you installed?

---

### Post by MooPi on 2010-08-17
I don't know about installing a full install along with wubi. Conceptually it sounds plausible. First off wubi is what you would call a virtual install inside windows. The entire install resides inside your windows partition. You can increase the size of your wubi but if your ready for a full install that is what I'd recommend. The swap is a small partition generally created during install that is used for page filing. This helps when your memory gets maxed out or your using a memory intensive application. The standard swap size is 1 1/2 the amount of ram your system contains. 

Howto make your wubi full time partition.
[http://ubuntuforums.org/showthread.php?t=438591]("http://ubuntuforums.org/showthread.php?t=438591")

---

### Post by cpmman on 2010-08-17
[***_Wubi Guide_***]("https://wiki.ubuntu.com/WubiGuide") includes many variants of resizing, repartitioning and separating.

---

### Post by mabynke on 2010-08-17
Thank you for your tips, MooPi and cpmmam!

> **GaryTheCat said:**
> Did you click "Install inside windows" when you installed?

I don't remember, but I found the Ubuntu hard drives (root and swap) as .disk-files in C:\ubuntu\disks, so i take it it's inside Windows.

I think I'll go for a complete installation, probably with a USB drive. Is there an easy way to keep my programs and files in the new install?

---

### Post by GaryTheCat on 2010-08-17
It sounds like this is what you're after

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by mabynke on 2010-08-18
Thanks for the link, but I think I've decided to make a new, clean install. Now I have some other problems. When asked where to install Ubuntu on the disk (In the boot installer) I could only take disk space from the original system restore partition, and not from the Windows partition. Thinking I was never going to use the restore anyway, I accepted that, and was planning to give Ubuntu more space later. Later, though, I went back to oversee my settings. I saw (not surprisingly) that a small part of the restore partition was made into free space. What surprised was that the 'Install Ubuntu along with the other OS-es' option was not checked, and the 'Erase the entire hard drive and install Ubuntu on it' was. This made made me so afraid of my entire hard drive getting formatted that I canceled the installation.
Why did the installer change the option of what to do, and was it really going to format my entire hard drive? I tried changing it back to the dual-boot option, and then go back again. The same happened that time.
I'm now going to double check that I have everything backed up before I do anything else.

---

### Post by silverglade00 on 2010-08-18
You probably want to shrink your Windows partition from within Windows and then boot up the Ubuntu CD and tell it to use available space.

---

### Post by Dreigo42 on 2010-08-18
I had this issue too. I simply made a list of the extra programs I had installed, Saved all my personal stuff(pictures,docs,music,ect) to my USB key, and did a clean install. Didn't want to completely remove windows so I used the basic partitioning step in the install to set up a dual boot. 
After that I realized the install finished, I ran sudo apt-get install (programs from list) and that reinstalled everything I had. Gotta love repositories. Anyway, Ubuntu saw windows as another removable media so I didn't even need my usb key. Just copied my stuff from the wubi in windows their respective places in my new home folder. 
I un-installed wubi after that and have never had a problem since.

Edit- forgot to add that the dual boot was set up by choosing the "Install side by side option" You could then adjust the slider to adjust the sizes of the partitons. Just made sure to leave enough space for windows. Windows did a check upon the its next start-up and everything came out fine.

---

### Post by mabynke on 2010-08-18
> **Dreigo42 said:**
> I had this issue too. I simply made a list of the extra programs I had installed, Saved all my personal stuff(pictures,docs,music,ect) to my USB key, and did a clean install. Didn't want to completely remove windows so I used the basic partitioning step in the install to set up a dual boot. 
After that I realized the install finished, I ran sudo apt-get install (programs from list) and that reinstalled everything I had. Gotta love repositories. Anyway, Ubuntu saw windows as another removable media so I didn't even need my usb key. Just copied my stuff from the wubi in windows their respective places in my new home folder. 
I un-installed wubi after that and have never had a problem since.

Edit- forgot to add that the dual boot was set up by choosing the "Install side by side option" You could then adjust the slider to adjust the sizes of the partitons. Just made sure to leave enough space for windows. Windows did a check upon the its next start-up and everything came out fine.
You didn't go back in the installation process and see what the settings were set to? When I did, it had changed from 'Install side by side' to 'Use entire hard drive'. That's why I was afraid of continuing.
Also, about the slider you are talking about. I tried it, but I could only take from the recovery partition to give space to Ubuntu, I couldn't take from the Windows-partition.

---

### Post by Dreigo42 on 2010-08-18
Sorry about that. I forgot that most computers come with a recovery image partition. I like to use entire disks when possible. Thats probably why I didn't have an issue. I am sure that there is a way to do it using the advanced setup option on that side but I never really figured that part out. It may be easier to readjust the sizes in Windows. Using their disk managment would prevent any possible issues and you could leave the space you want Ubuntu on as unallocated. The Installer would probably use that space if you choose "Use largest continuous free space" I'm not certain but setting them up in Windows would prevent you accidentally cutting the windows partition too small.

FYI disk management is in control panel->administrative tools->computer management

---

### Post by mabynke on 2010-08-18
I tried that now, but I think somethings wrong.
On the attached image, you can see that I can't reduce it more than 0 MB, in other words nothing. I just ran disk defragmentation, so there shouldn't be fragmentatated files laying around.
You guys have any ideas what to do?
Installing Ubuntu turned out to be a little more difficult than I imagined.

---

### Post by bcbc on 2010-08-18
> **mabynke said:**
> I tried that now, but I think somethings wrong.
On the attached image, you can see that I can't reduce it more than 0 MB, in other words nothing. I just ran disk defragmentation, so there shouldn't be fragmentatated files laying around.
You guys have any ideas what to do?
Installing Ubuntu turned out to be a little more difficult than I imagined.

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

that link discusses this issue

---

### Post by mabynke on 2010-08-18
Interesting link, with a lot of great tips. However, I'm a little concerned disabling system restore points and hibernation (I've had trouble re-activating hibernation before). I thought the reason why system files couldn't be moved was that they were in use by the OS. Can this be solved by defragmentating from a live CD? Is it possible to defragmentate my Windows partition using Ubuntu?

---

### Post by bcbc on 2010-08-18
> **mabynke said:**
> Interesting link, with a lot of great tips. However, I'm a little concerned disabling system restore points and hibernation (I've had trouble re-activating hibernation before). I thought the reason why system files couldn't be moved was that they were in use by the OS. Can this be solved by defragmentating from a live CD? Is it possible to defragmentate my Windows partition using Ubuntu?

No, not that I am aware of.

I can understand you're hesitant to do that - I would be too. I recommend backups prior to attempting this.

---

