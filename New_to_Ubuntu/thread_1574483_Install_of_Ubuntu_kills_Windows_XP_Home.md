---
title: "Install of Ubuntu kills Windows XP Home"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by NickN002 on 2010-09-14
Hello,

I'm brand new to Ubuntu and I searched the forums for answer to this, but the solutions I tried haven't worked. I installed Ubuntu 10.0.4 Netbook Remix on my Toshiba NB205. I installed Linux so that I could have a dual boot machine. At the grub screen when I select the Windows XP Home partition, Windows starts and then immediately crashes and then returns to the BIOS start-up. From my reading of the forums, I think that my master boot record is messed up. I don't have a Windows XP home install CD since it came preloaded and it did not come with an external CDROM. I still have a bootable USB with Linux on it. Luckily the data (documents, etc.) are backed up to the cloud.

I tried starting using a Windows XP Professional CD (to try to repair the problems) but even that leads to the blue screen of death.

Thanks.
Nick

---

### Post by mastablasta on 2010-09-14
how did you install dual boot? did you defragment the windows partition before resizing it? 
 
you should be abel to get a recovery CD and then use it to reinstall the whole system and then to try again to install Ubuntu.
 
maybe there is a less messy version...
 
but basically grub replaces the windwows MBR and to my experience installing it dual boot is really smooth in winxp. as long as you follow all precautions: running chkdsk and then defragmenting the disk before resizing it.

---

### Post by Jazzy_Jeff on 2010-09-14
You will probably have to start over. Make sure all your important things are backed up. You should be able to do a recovery for your Windows XP. Once that is done use Windows to shrink your XP partition.

---

### Post by tony.Young on 2010-09-14
> **NickN002 said:**
> Hello,

I'm brand new to Ubuntu and I searched the forums for answer to this, but the solutions I tried haven't worked. I installed Ubuntu 10.0.4 Netbook Remix on my Toshiba NB205. I installed Linux so that I could have a dual boot machine. At the grub screen when I select the Windows XP Home partition, Windows starts and then immediately crashes and then returns to the BIOS start-up. From my reading of the forums, I think that my master boot record is messed up. I don't have a Windows XP home install CD since it came preloaded and it did not come with an external CDROM. I still have a bootable USB with Linux on it. Luckily the data (documents, etc.) are backed up to the cloud.

I tried starting using a Windows XP Professional CD (to try to repair the problems) but even that leads to the blue screen of death.

Thanks.
Nick
How did you install ubuntu?  Wubi? USB?  according to my experience, I suggest you install it by wubi.

---

### Post by Jazzy_Jeff on 2010-09-14
> **tony.Young said:**
> How did you install ubuntu?  Wubi? USB?  according to my experience, I suggest you install it by wubi.

? I would only recommend Wubi if you want to try it out. Dual boot is always better.

---

### Post by oldfred on 2010-09-14
This may show if something is messed up with your windows. The windows MBR only passes booting to the windows PBR partition boot sector. Grub bypasses the MBR and jumps to the windows PBR to boot windows. If you are getting an error it is in the PBR, boot.ini or ntldr files.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Kixtosh on 2010-09-14
If the worst comes to the worst, and you have to re-install everything, then in my experience, Toshiba laptops come with a Recovery and Applications disk (CD or DVD) that you need to insert in a bootable external drive. Then start the machine while holding down the C key (or use boot options from the BIOS to make sure the CD/DVD drive boots first), and you should get a prompt that enables you to re-install everything to the initial factory settings, which includes wiping the hard drive completely.

Otherwise, I currently dual boot two Toshiba Portégé laptops: ($one old one, and one fairly new one; with W2K and Win XP Pro respectively. Both were flawless installs.

1) First, I defragmented the hard drive within the Windows O.S., repeating the process at least twice (three or four times total). It gets faster after the first time, by the way.

2) Then, I allowed the Live CD installation process to resize the properly defragmented Windows partition automatically (although I may have adjusted the size of the Windows partition to shrink it down a little manually, using the slider that shows up during that process, on the lower half of the screen).

Both Windows O.S.'s work perfectly, and better than before (no more accumulated junk), and both Xubuntu/Ubuntu 10.04 O.S.'s work perfectly as well.

I'm mostly using Xubuntu/Ubuntu on both machines at the moment, but I have the dual boot capability if I need something in Windows too (really only on the newer laptop - I almost never boot W2K any more on the older one).

It really shouldn't be much of a problem, but you may not be able to use all the keyboard "hotkey" shortcuts (using the Fn key) when using Ubuntu.

---

### Post by NickN002 on 2010-09-15
Thank you all for the suggestions. I unfortunately did not defrag or run chkdsk prior to making the new partition from the USB. With the help of a co-worker in IT, we'll try recovering Windows first. If that doesn't work, we'll wipe and re-install. I wonder if there was an error on the disk before the new partition was made. I;ll be sure to run chdsk and defrag more often in the future. Thanks again.
 
Nick

---

### Post by Kixtosh on 2010-09-15
Nick, if you have backed things up, there really is nothing to worry about (except the time it takes to reload XP, and then reload the multiple updates, including mandatory restarts). I just did all of that on my Portégé, and it is a bit of a pain, but it's not all that daunting.

However, there's probably a good chance you'll get Windows back, once you fix the Master Boot Record (MBR). I've done this before with W2K, and it's very easy to do. It only takes minutes to complete from the start of the whole process to the finish, but it does not remove your Ubuntu installation or change any partitions.

if you cannot get Windows XP to boot up again and have to opt for the full install procedure instead, this will wipe the hard drive completely, including the Ubuntu partition.

I certainly wouldn't panic. Now, go check to see if you can find the Toshiba Recovery CD! ;)

---

