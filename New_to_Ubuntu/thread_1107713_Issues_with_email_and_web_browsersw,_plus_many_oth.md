---
title: "Issues with email and web browsersw, plus many others..."
date: 2009-03-27
forum: New to Ubuntu
---

### Post by cj_mack on 2009-03-27
Hi,

I have finally got fed up with XP, and switched to Ubuntu.  I still have dual boot setup, as I've only been using Ubuntu for 1 day.

Today I installed Wine, so as I can run my email program and web browser.  I run portableapps.com which includes Firefox portable and Thunderbird portable.

I can run and use these programs, however they are rather slow, and the fonts show really badly, with bits missing out of the letters.  It is still readable, just annoying.  Is this caused by a windows app on Wine, or something else?

If I am to switch over to an Ubuntu based email app, what would you suggest?  I need to send/receive from multiple POP accounts, have a calendar, and be able to set task lists.  As much as I like having the portable apps, I can leave it if needed.  I also need to be able to import data from Thunderbird 2.0.0.19

I also need a program to play my music on.  I quite like using Winamp, as I have used it for many years, is stable, and can handle a large playlist.  Is there something like this and is stable that runs on Ubuntu?  I will be installing VLC shortly to play my video files.

Also, I cannot seem to be able to install Adobe Flash player into the Firefox version that comes with Ubuntu, not sure why?

All hardware devices are working fine.

I'm sure I will find other things that I wish to work out, but until then, this is it.  I appreciate any help.

Thanks,


Sam.

PC details in case they help:
AMD 64bit AM2
2GB RAM
Windows XP SP3 - Main boot drive (SATA)
Ubuntu 8.10 & Grub - IDE secondary drive (BIOS booting from here)

---

### Post by leonardo_neo on 2009-03-27
> Today I installed Wine, so as I can run my email program and web browser. I run portableapps.com which includes Firefox portable and Thunderbird portable.


Firefox is already given with the default package of Ubuntu. Why would you want to run it through wine?? 

> If I am to switch over to an Ubuntu based email app, what would you suggest? I need to send/receive from multiple POP accounts, have a calendar, and be able to set task lists. As much as I like having the portable apps, I can leave it if needed. I also need to be able to import data from Thunderbird 2.0.0.19


Again the default email client 'evolution' can do all the things you desire for. You can also run thunderbird on Ubuntu if you want.

> I also need a program to play my music on. I quite like using Winamp, as I have used it for many years, is stable, and can handle a large playlist. Is there something like this and is stable that runs on Ubuntu

The default player rhythmbox is good enough, but if you are so comfortable with Wimamp, then you can install XMMS, which looks and feels like Winamp.

> Also, I cannot seem to be able to install Adobe Flash player into the Firefox version that comes with Ubuntu, not sure why?


Go to this link........
> [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

From dropdown box, select the last .deb package, download it, save it on comp, and just double click it. It will be installed.

Hope this helps....

:)

---

### Post by jakupl on 2009-03-27
> **cj_mack said:**
> 
If I am to switch over to an Ubuntu based email app, what would you suggest?  I need to send/receive from multiple POP accounts, have a calendar, and be able to set task lists.  As much as I like having the portable apps, I can leave it if needed.  I also need to be able to import data from Thunderbird 2.0.0.19)

just install thunderbird
goto terminal (applications --> accessories --> terminal) and enter:
```
sudo apt-get install thunderbird
```
and it will show up under applications --> internet
Or you can use the default one called Evolution, however I'm not sure about importing a thunderbird profile into Evolution.
> **cj_mack said:**
> 
I also need a program to play my music on.  I quite like using Winamp, as I have used it for many years, is stable, and can handle a large playlist.  Is there something like this and is stable that runs on Ubuntu?  I will be installing VLC shortly to play my video files.
)
I use rhytmbox for that, rhytmbox is default on ubuntu, so it is allready installed, it looks kind of like iTunes.

> **cj_mack said:**
> 
Also, I cannot seem to be able to install Adobe Flash player into the Firefox version that comes with Ubuntu, not sure why?


go to synaptic package manager (system --> administration --> synaptic package manager) and search for ubuntu-restricted-extras and then install it. That will take care of everything for you (including being able to play mp3, avi and other stuff).

---

### Post by cj_mack on 2009-03-27
Hi,

Thanks for your help already.  I was using the portable version of Firefox in the mean time as it had all of my favorites etc on it.  I am currently transferring them.

My next questions:
How do I backup my emails, bookmarks and other important info?  I used to just copy the actual data files to separate locations on the PC under XP.  I am slowly getting my head around the Unix filesystem, so if I need to do this I will be able to.

Also, whenever I am in Ubuntu, the light on my floppy drive is constantly on.  Under XP it doesn't glow.  I know floppy drives are ancient technology, but I do need to use them occasionally.  Am I able to use it?  It does not show in the file browser.

Thanks.

---

### Post by plucky on 2009-03-27
> Also, whenever I am in Ubuntu, the light on my floppy drive is constantly on. Under XP it doesn't glow. I know floppy drives are ancient technology, but I do need to use them occasionally. Am I able to use it? It does not show in the file browser.

The floppy driver was not loaded in Intrepid Ibex.See this [thread](http://ubuntuforums.org/showthread.php?t=952387&highlight=floppy) for how to load the driver.

Also to make the floppy available to the user,you need to add this line to the **/etc/fstab** file.```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
 and create the mount point with the command from a terminal ```
sudo mkdir /dev/floppy0
```

> How do I backup my emails, bookmarks and other important info? I used to just copy the actual data files to separate locations on the PC under XP. I am slowly getting my head around the Unix filesystem, so if I need to do this I will be able to.



All that information is stored in your /home directory,usually in .hidden files.Just backup those files,preferably to a different partition on a separate disk.


Good Luck

---

