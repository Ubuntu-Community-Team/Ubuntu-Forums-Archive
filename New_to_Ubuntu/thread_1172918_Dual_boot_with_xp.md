---
title: "Dual boot with xp"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by aravindc26 on 2009-05-29
I have been using ubuntu for 1 month now, but now I need xp to run visual studios. But I cannot remove ubuntu so please tell me how to dual boot xp with ubuntu.
Please note that I am using Ubuntu not xp.

---

### Post by lisati on 2009-05-29
Before we begin: it's usually easier to install XP before Windows, but it's not impossible to do it the other way round.

Presumably you have a legal copy of an XP installation disk or a recovery partition on your computer.

---

### Post by aravindc26 on 2009-05-29
I dont have recovery partion

---

### Post by s.fox on 2009-05-29
Hi,

You could try following [this]("http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/") guide,  though I have never done what you are attempting.

Good look and I hope you get your dual boot running.

-Ash R

---

### Post by lisati on 2009-05-29
> **aravindc26 said:**
> I dont have recovery partion

Then you will need a Windows installation disk.

Have a look at the tutorial mentioned by Ash R: feel free to ask us questions.

---

### Post by s.fox on 2009-05-29
Hi again,

Just a quick reminder,   **BACKUP** all important data before you do anything.  I would hate you to lose anything.

-Ash R

---

### Post by aravindc26 on 2009-05-29
Thanks guys,

I have a doubt , I have ubuntu 8.10 installation cd, Will that help . does the cd contain gparted

---

### Post by stunningman on 2009-05-29
well if your are using ubuntu from past two months then i think you have not done much with ubuntu yet.

to make long thing short.just format your drive,say you have 160gb then divide it into 30 gb each.keep your first partition for windows and install windows xp or vista first. then leave the next partition and then install ubuntu on alternate partition in this way your dual boot will be less cluttered and easy to use.and there will also be no effect on speed.

[http://blogiyao.blogspot.com](http://blogiyao.blogspot.com)

---

### Post by stunningman on 2009-05-29
and yes ubuntu have a partitioner which runs even before you decide to install ubuntu after windows.

[http://blogiyao.blogspot.com](http://blogiyao.blogspot.com)

---

### Post by tacantara on 2009-05-29
Rather than try to create a dual-boot machine after installing Ubuntu, I went with the option to install a vitrual machine.  VirtualBox runs XP quite well, and you don't have to leave one OS to use the other.  I suppose that there are advantages to dual-boot, but my virtual machine setup works for me.  I even have access to the essential hardware when running XP in virtual mode (CD/DVD drive, USB ports, etc.).
 
aravindc26:  If you decide to check out the virtual machine option, download VirtualBox from their website.  The download is a .deb package, so installation will go smoothly.

---

### Post by aravindc26 on 2009-05-29
thank you

---

### Post by powel212 on 2009-05-29
> Rather than try to create a dual-boot machine after installing Ubuntu, I went with the option to install a vitrual machine.

I am 100% in agreement with tacantara

here is an example of windows in Ubuntu on Sun VirtualBox

[http://www.flickr.com/photos/sunrisefoto/3567107074/](http://www.flickr.com/photos/sunrisefoto/3567107074/)

I run Photoshop this way and sink my ipod in iTunes this way. It is way better than dual booting. I used to do that but never again.

Here is the VirtualBox site.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Powel

Please try this before wasting a bunch of time reverse engineering a dual boot. i promise you will be happier.

---

### Post by Jive Turkey on 2009-05-29
I have gone through what you are talking about several times.  

Once you grok the restoring grub part, its super easy.  I have some suggestions.

1) I have used vmware to run XP with VS2008 and it worked fine, not noticabley slower than XP on real hardware but I havent really benchmarked it or anything.

2) Consider using windows 7 RC instead of XP, you can use the free release candidate until June 2010, you can download it from microsoft.  It takes about two days of cycling through windows update and rebooting to get an XP sp2 install up to date.  Windows 7 only takes a cycle or two.

For dual booting, these are the steps.
1) Make a partition for windows if you don't have one using a live CD.  Be sure to back up important files on your disk before resizing any partitions.  I've never had it go awry and destroy data using gparted but it can happen.  If you format the windows partition as ntfs using gparted it will be easier to identify when you run the windows installer reducing the risk of data loss.  Possibly consider getting an additional HDD.

2) Install the windows

3) Boot your ubuntu live CD and restore grub.  There are lots of good Howtos google it.  One thing to watch out for is how ubuntu names your drives and partitions vs how grub names them.  For example Ubuntu says that on my two HDDs I have /dev/sda1, sda2, sda3 for one drive and /dev/sdb1, sdb2, sdb3
My ubuntu is on sdb1 (and so is grub) When I installed windows 7 on sda1 after ubuntu my bios preferred to use that drive until I changed the bios setting to prefer the other one and it booted ubuntu.  Notice that grub uses hd0,0 hd0,1 hd0,2 at any rate grub sees my sda drive as hd1 not hd0, probably because I changed the boot order in my bios.

in my /boot/grub/menu.lst file I had to modify the windows option (windows 7 RC) to get it to boot.  Mine looks like this now:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the 
# Debian ones.

title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows7 (loader)
rootnoverify	(hd1,0)
chainloader	+1

```

If you hit any hitches I'd be happy to help you work it out.

---

### Post by powel212 on 2009-05-29
> It takes about two days of cycling through windows update and rebooting to get an XP sp2 install up to date.

I can't disagree with running win7 in a virtualbox. I do it. But it is heavier than xp. Yes you can turn off all the bells and whistles and it gets pretty light but if you already own xp and you want to use it you can grab the SP3 standalone cd from the MS site burn it to cd and run it instead of the online update which is crazy slow. The last time I did a repair job on an xp box it took 26Hours to install and update, which is why i use the standalone SP3 instead now. With it you can finish an xp install in a virtualbox in about 60 min.

SP3 Download site
[http://www.microsoft.com/windows/products/windowsxp/sp3/default.mspx](http://www.microsoft.com/windows/products/windowsxp/sp3/default.mspx)

Powel

---

### Post by aravindc26 on 2009-05-29
I have 1 gb ram and 80gb hard disk and pentium d processor will that do for virtual box

---

### Post by powel212 on 2009-05-29
It is enough if you run xp in the Virtual Box. 

When you run virtualBox you have to tell it how much RAM to assign to the "guest" OS in this case we'll say XP. So if you have a gig you could give xp 400 and you will still have 600 for Ubuntu which is lots. The Guest xp OS will also create a scratch disc within the disc space you allocated as well. So it should be totally safe. A dual boot will use more hard disk than running a virtualbox and the virtual box disc space is dynamic, (it expands on demand). And you can even assign the drive space within virtualbox to an external drive or even a flash drive. 


But If I may suggest, RAM is cheaper than it has ever been and performance for dollars buying more RAm can not be beat. I have 6 Gigs in mine and might even buy more. I was at the store yesterday and a gig was priced at less than 20Bucks. It's crazy.

Powel

---

### Post by aravindc26 on 2009-05-29
> **powel212 said:**
> It is enough if you run xp in the Virtual Box. 

When you run virtualBox you have to tell it how much RAM to assign to the "guest" OS in this case we'll say XP. So if you have a gig you could give xp 400 and you will still have 600 for Ubuntu which is lots. The Guest xp OS will also create a scratch disc within the disc space you allocated as well. So it should be totally safe. A dual boot will use more hard disk than running a virtualbox and the virtual box disc space is dynamic, (it expands on demand). And you can even assign the drive space within virtualbox to an external drive or even a flash drive. 


But If I may suggest, RAM is cheaper than it has ever been and performance for dollars buying more RAm can not be beat. I have 6 Gigs in mine and might even buy more. I was at the store yesterday and a gig was priced at less than 20Bucks. It's crazy.

Powel
THANK YOU [powel212]("http://ubuntuforums.org/member.php?u=699539") .

One more thing I am an Indian things are different here. Only one out of thousand know about Ubuntu.
Here RAM is very expensive. Can't help it, recession....!!

---

### Post by Jive Turkey on 2009-05-29
I didn't know you were in India, I wouldn't try windows7 on that hardware.  I'm not sure if the win7 RC is available there or not.  Check the system requirements for any virtualization programs before you try to install.  We can still help with dual booting too.

---

### Post by iKevin09 on 2009-05-29
I'm running a dual-boot computer with Windows XP and Ubuntu 9.04 Jaunty. First I did a complete wipe of Vista and upgraded to XP.
I made the XP Parition 30 GB and the rest is dedicated to Ubuntu.
I installed XP on the 30 GB partition, and installed drivers and such.
After I was satisfied with XP, I popped in the Ubuntu disc and restarted my computer
I then was prompted to select a language, and had a selection to make. I chose Install Ubuntu. I chose my Hitachi 130GB HDD and installed Ubuntu on the rest of the partition.
Now when I boot my computer, Grub automatically spotted that Windows is also on here, so it gave me a choice of 3 different modes of Ubuntu, then "Other Operating Systems" and Microsoft Windows XP Professional was on below it. So it's quite simple.

Backup data
Wipe out HDD
Install Windows
Install Ubuntu
Instant dual-boot

---

### Post by andrew.46 on 2009-05-29
Hi aravindc26,

> **aravindc26 said:**
> I have 1 gb ram and 80gb hard disk and pentium d processor will that do for virtual box

I have the same ram and disk size but a processor substantially less powerful than the Pentium D and I have no problem running windows XP, although I have not tried Windows 7. I use VirtualBox OSE but I know many prefer the non-free version.

Andrew

---

### Post by aravindc26 on 2009-05-29
> **andrew.46 said:**
> Hi aravindc26,



I have the same ram and disk size but a processor substantially less powerful than the Pentium D and I have no problem running windows XP, although I have not tried Windows 7. I use VirtualBox OSE but I know many prefer the non-free version.

Andrew
what is the difference between opensource version and non-free version ?
does it differ in features?
is it necessary to have genuine copy of windows to run virtual box?

---

### Post by andrew.46 on 2009-05-29
Hi aravindc,

> **aravindc26 said:**
> what is the difference between opensource version and non-free version ?
does it differ in features?

There are 2 major differences:

[LIST=1]
[*]OSE version releases the full source code, while the PUEL version does not.
[*]OSE version does not have usb support, while the PUEL version does.
[/LIST]

The *full* list of differences can be seen here:

Open Source VirtualBox and other editions
[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

It is a little sad that so many people abandon their open source principles *so quickly* and use the closed source version.

> is it necessary to have genuine copy of windows to run virtual box?

Virtualbox itself does not care if the copy of windows is genuine or not. There will only be the usual problems of windows activation and 'genuine copy' checks = windows problems :-).

All the best,

Andrew

---

### Post by aravindc26 on 2009-05-29
Thank you very much andrew.
I'll stick to opensource principles, that is why I abandoned windows.
but situation demands me to use xp,
can i run visual studios with wine ?

---

### Post by Jive Turkey on 2009-05-31
> **aravindc26 said:**
> Thank you very much andrew.
I'll stick to opensource principles, that is why I abandoned windows.
but situation demands me to use xp,
can i run visual studios with wine ?

I doubt it will work with wine, its not just one app either it needs all the latest .NET stuff and it will make you install SQL server express as well.  I think you'd be happier dual booting.

---

### Post by powel212 on 2009-05-31
> One more thing I am an Indian things are different here. Only one out of thousand know about Ubuntu.
Here RAM is very expensive. Can't help it, recession....!!

I live in Taiwan where RAM is made. Let me now if you think there may be an opportunity here. Send me a private message if you are interested in talking about doing some business. I work in import export and would be very interested in discussing sending RAM to India.

Powel

---

### Post by t_k_majumdar on 2009-05-31
Hi aravindc26 -

You received good advices from experienced ubuntu users. I am also a relatively new-comer to the ubuntu-world like you. I can narrate my own experience about this matter.I set-up a dual-boot with XP and ubuntu in a computer far less resourceful and older than yours. I was getting problem if I need to change a partition or delete an os. Ultimately, I solved the problem in this way which satisfied my needs:

1. Downloaded GAG, The graphical boot manager, Current version: 4.10 from [http://gag.sourceforge.net/download.html](http://gag.sourceforge.net/download.html)

2. Unzipped the contents in C:\ drive in a separate folder.

3.Run appropriate program ( there are 4 of them; choose by trial and error!) from that folder to make a bootable floppy.

4. Rebooted with the floppy.

5. Configured it by clicking set-up icon, added windows os and saved the result in floppy.

6. All the above steps were from within windows os.

7. Now, I installed Ubuntu 9.04 aka Jaunty Jackalope in a separate partition, taking care to install the grub in a separate small boot partition created for this purpose during installation process.

8. Rebooted with the floppy. Added now the ubuntu boot partition with the set-up icon of GAG boot manager and saved the result in floppy again.

9. With floppy in, I can now get a nice graphics menu to choose from windows or ubuntu. No problem at all. I can easily delete any os simply by deleting the partition or format any partition without affecting the other os. Without the floppy, the system automatically boots into the windows but that default option can be changed. 

At least, I am happy with this arrangement. But, without floppy drive, well, I don't know whether it would work or not. I think, gag can be run from Pendrives. It can be installed in hard disk also but I got problems with that.

Now, to your vital point. I installed window first, then ubuntu. In your case, when you install window after ubuntu, window will overwrite the bootloader. But, with a little manipulation with gag, you can add ubuntu later. Best procedure: Back-up all important data, install window, install then ubuntu with grub in a separate small partition, install gag and enjoy.

My computer specs: Dell optiplex GX1 , 500 mHz, 80 GB HDD, 500 MB RAM. I run both systems at will and faced no problem so far.

Incidentally, I am now liking ubuntu so much that I feel no reason to use windows os again and I have not booted into it for a long time now.

---

### Post by aravindc26 on 2009-05-31
> **t_k_majumdar said:**
> Hi aravindc26 -

You received good advices from experienced ubuntu users. I am also a relatively new-comer to the ubuntu-world like you. I can narrate my own experience about this matter.I set-up a dual-boot with XP and ubuntu in a computer far less resourceful and older than yours. I was getting problem if I need to change a partition or delete an os. Ultimately, I solved the problem in this way which satisfied my needs:

1. Downloaded GAG, The graphical boot manager, Current version: 4.10 from [http://gag.sourceforge.net/download.html](http://gag.sourceforge.net/download.html)

2. Unzipped the contents in C:\ drive in a separate folder.

3.Run appropriate program ( there are 4 of them; choose by trial and error!) from that folder to make a bootable floppy.

4. Rebooted with the floppy.

5. Configured it by clicking set-up icon, added windows os and saved the result in floppy.

6. All the above steps were from within windows os.

7. Now, I installed Ubuntu 9.04 aka Jaunty Jackalope in a separate partition, taking care to install the grub in a separate small boot partition created for this purpose during installation process.

8. Rebooted with the floppy. Added now the ubuntu boot partition with the set-up icon of GAG boot manager and saved the result in floppy again.

9. With floppy in, I can now get a nice graphics menu to choose from windows or ubuntu. No problem at all. I can easily delete any os simply by deleting the partition or format any partition without affecting the other os. Without the floppy, the system automatically boots into the windows but that default option can be changed. 

At least, I am happy with this arrangement. But, without floppy drive, well, I don't know whether it would work or not. I think, gag can be run from Pendrives. It can be installed in hard disk also but I got problems with that.

Now, to your vital point. I installed window first, then ubuntu. In your case, when you install window after ubuntu, window will overwrite the bootloader. But, with a little manipulation with gag, you can add ubuntu later. Best procedure: Back-up all important data, install window, install then ubuntu with grub in a separate small partition, install gag and enjoy.

My computer specs: Dell optiplex GX1 , 500 mHz, 80 GB HDD, 500 MB RAM. I run both systems at will and faced no problem so far.

Incidentally, I am now liking ubuntu so much that I feel no reason to use windows os again and I have not booted into it for a long time now.

Thanks for your concern.
But I use ubuntu.
I want to use xp as my 2nd os

---

