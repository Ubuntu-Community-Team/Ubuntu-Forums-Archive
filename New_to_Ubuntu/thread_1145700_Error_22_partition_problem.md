---
title: "Error 22 partition problem"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by isee on 2009-05-01
Gateway MX 6441
I installed Intrepid and was working fine, Broadcom wireless and all (except no playing movies, but will deal with that later), and so tried to use Gparted to get some partitions cleaned up.

Now I get Error 22 when turning on the laptop, obviously done something wrong.

I can't even boot into windows now.

Any recovery?

Will a disk format erase all partitions?
If so, if I do an install of Intrepid using the whole drive, will I then have my whole HD back?
Can I install Windows on a partition after I install Linux, or do I have to install Windows first? (gf will not let me have Linux alone)

No data can be lost, as this laptop was bought for learning purposes, so as long as the hard drive doesn't fail, no problems. (Except for the fact that reinstalling windows takes HOURS and HOURS of downloading and rebooting, going from SP1 to SP3, barf)

Love learning

Cheers

---

### Post by jbrown96 on 2009-05-01
To understand Error 22, you must first understand how grub works.

There is a very small part on the very beginning of your hard drive called the MBR (master boot record). This tells your computer what it should do when it boots. The problem is that this section is so small that it can't really do anything. It's really a pointer to another location. The MBR points to the /boot directory on your linux partition for more information on what to do. From there you can boot linux or any other operating systems on your computer that are registered with grub. 

Your problem is that either the linux partition has been deleted or renamed, so the pointer from the MBR doesn't point to a valid location. 


How you can fix it:
1) Vista boot disk. Boot from it and do a recovery. It will fix the MBR to point to Vista. You can then install ubuntu again if you wish.


Alternate:
1) Reinstall Ubuntu to the same partition. This will overwrite your MBR and everything should work properly. 

If your Gf wants Windows, then you shouldn't use the whole drive. Since Ubuntu expects to see multiple operating systems with Grub, it is generally preferable to install Windows first. This solves a lot of problems of having to manually install grub. 


Your best bet is to reinstall ubuntu, being careful not to use the Vista partition to install. 

For your video playback problems, go into synaptic (sys--->admin-->synaptic)--->settings--->repositories. Make sure all the repositiories (main, multiverse, etc.) are enabled. Refresh your sources, then search for and install ubuntu-restricted-extras and vlc. You shouln't have any problems playing video.

---

### Post by meierfra. on 2009-05-01
> Your best bet is to reinstall ubuntu,
I disagree. Unless you deleted the Ubuntu partition there is no need to reinstall Ubuntu. You just need to reinstall Grub:

Boot from the Ubuntu LiveCD, open a terminal (Applications->Accessories->Terminal) and type

```
sudo grub 
```

and at the "grub>" prompt.



```
 find /boot/grub/stage2 
```

This will return (hdX,Y), where X and Y are some numbers, like (hd1,0)
(if it returned 'file not found', try  'find /grub/stage2' and  'find /stage2')


Still at the "grub>" prompt:


```
root (hdX,Y)
setup (hdX)
quit

```

(here X and Y need to be replaced by the numbers you got from "find ... stage2")

Reboot, with the bios set to boot from the Ubuntu drive.


**If this did not work,** lets have a closer look at  your partitions:

Boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal  and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by jbrown96 on 2009-05-01
> **meierfra. said:**
> I disagree. Unless you deleted the Ubuntu partition there is no need to reinstall Ubuntu. You just need to reinstall Grub:

Boot from the Ubuntu LiveCD, open a terminal (Applications->Accessories->Terminal) and type

```
sudo grub 
```

and at the "grub>" prompt.



```
 find /boot/grub/stage2 
```

This will return (hdX,Y), where X and Y are some numbers, like (hd1,0)
(if it returned 'file not found', try  'find /grub/stage2' and  'find /stage2')


Still at the "grub>" prompt:


```
root (hdX,Y)
setup (hdX)
quit

```

(here X and Y need to be replaced by the numbers you got from "find ... stage2")

Reboot, with the bios set to boot from the Ubuntu drive.


**If this did not work,** lets of a closer look at  your partitions:

Boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal  and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

I agree meierfra. It is certainly possible to recover it if he/she hasn't deleted the partition. The thing is that it only takes about 20 minutes to reinstall Ubuntu, and it's dead simple. It's the path of least resistance.

---

### Post by meierfra. on 2009-05-02
Reinstalling Grub should only take 5 Minutes. But since this is a fresh install and you probably haven't spend much time customizing Ubuntu, reinstalling Ubuntu is of course also a valid option.

---

### Post by Didius Falco on 2009-05-02
I think the first thing I'd suggest is to boot with a Live CD, run ```
sudo blkid
sudo fdisk -l
``` to get a list of the UUID numbers and partitions, save that to a file, then run ```
gksu gedit
```, navigate to the /boot/grub/menu.lst file and check the UUID numbers from the blkid against the menu.lst file.

If the OP moved or resized partitions those numbers will change. I got burnt by this not that long ago and spent  enough time trying to figure it out that I'll likely never forget that particular lesson.

On Edit: Yeah, that script is very nice. Saves a lot of back and forth, collects all the info you need in one place - kudos to whoever wrote it. Now I just have to get into the habit of recommending it.

---

### Post by caljohnsmith on 2009-05-02
> **Didius Falco said:**
> 
kudos to whoever wrote it.
Funny you should wonder who wrote the Boot Info Script--the guy who's been helping out in this thread is the one who wrote it--meierfra. Big thanks to him for making such a useful script for us all to use. :)

Cheers,
John

---

### Post by isee on 2009-05-14
Thanks all!

Even if I didn't understand, it was pointing me in the right direction.

What I did was a reformat install, and I've got to say it was a lot less painfull than doing a MS full reinstall (as i dont have the app disks for this comp so start from sp1 with no drivers, have to do it manual, ummm 7 -8 hours, no joke)

from jbrown96 (Thank you)
```
For your video playback problems, go into synaptic (sys--->admin-->synaptic)--->settings--->repositories. Make sure all the repositiories (main, multiverse, etc.) are enabled. Refresh your sources, then search for and install ubuntu-restricted-extras and vlc. You shouln't have any problems playing video.       1 Week Ago 09:02 PM
```This introduced me to how to look for ummmm,  well what can you say after seeing Synaptic Package Manager for the first time except Thank You Ubuntu (and jbrown96)

Also enable:
libdvdread4
libdvdna4
libdvdcss2
(for 8.10)

Check this link for help
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

