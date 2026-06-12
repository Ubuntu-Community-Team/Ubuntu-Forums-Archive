---
title: "Problems installing lucid from live CD"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Kyley on 2010-09-04
So, last night, after a long time of meaning to do so, I finally downloaded the ISO for lucid. I' running vista now and I wanted to run it right off the disk, to try it out. When I load the disk I get a purple screen, the logo and some dots, dots go across for a bit, then I'm straight to the login screen...which is irritating because I never got to create a login so I can't log in, I've tried running it off the disk and instaling it, the only thing that deviates from the above is that before the dots, there's just a purple screen with what looks like a reel of film and a man inside a circle (very technical terms I know) which appears for a moment and if I press any key here I get a screen that looks like the fisrt image [here]("https://help.ubuntu.com/community/BootParameters") but is purple, and some of the otions are different.

I'm running vista on an inspiron 1525, 2gb ram :)

Anybody know what the problem is?

---

### Post by oldfred on 2010-09-04
Welcome to the forums.

The liveCD does not require a login as it is just a temporary system.

If you are having video issues. What video card do you have, if you can boot. If not f6 nomodeset or f4 may give you a session.
sudo lspci | grep VGA

I have nvidia & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
sudo nvidia-xconfig
Or it should be in System>administration>Hardware drivers.


Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

If you are going to install be sure to use the windows tools to shrink the Vista/7 partition.

---

### Post by Kyley on 2010-09-04
I don't think It's the video card, the problem is that it goes straight to the login page without all the welcome, set up stuff, maybe I'm just being thick, atm I'm trying to install it inside windows to get an account set up.

EDIT: when I can actually make it work I plan to do away with windows altogether

---

### Post by oldfred on 2010-09-04
Are you trying a wubi install inside the windows partition. If so you will not be able to remove windows without also removing the wubi install.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Full Disk install Lucid Graphical
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Install Screens shown with advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by NightwishFan on 2010-09-04
The Live CD is supposed to log in automatically. I believe if it does not the username is ubuntu and there is no password. I would like to ask did you download the Lucid 10.04.1 image or the stock one from April 2010? If you have the old one, get the new point release it has a lot of bug fixes.
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by Kyley on 2010-09-04
It was the most recent one from the download page, the username:ubuntu thing hasn't worked, but I think nightwish understands the problem

---

### Post by NightwishFan on 2010-09-04
I was going to suggest using safe graphics mode, however that option seems to have been removed. So I am stumped.

---

### Post by kmsalex on 2010-09-04
try the alternate install cd, you won't be able to try it out first though, it'll send you straight to a text installer. If you want you could get [virtual box]("http://www.virtualbox.org/") for windows and try to boot the live cd in that but it will be *very* slow.

---

### Post by sandyd on 2010-09-04
> **Kyley said:**
> So, last night, after a long time of meaning to do so, I finally downloaded the ISO for lucid. I' running vista now and I wanted to run it right off the disk, to try it out. When I load the disk I get a purple screen, the logo and some dots, dots go across for a bit, then I'm straight to the login screen...which is irritating because I never got to create a login so I can't log in, I've tried running it off the disk and instaling it, the only thing that deviates from the above is that before the dots, there's just a purple screen with what looks like a reel of film and a man inside a circle (very technical terms I know) which appears for a moment and if I press any key here I get a screen that looks like the fisrt image [here]("https://help.ubuntu.com/community/BootParameters") but is purple, and some of the otions are different.

I'm running vista on an inspiron 1525, 2gb ram :)

Anybody know what the problem is?
check the md5 of the downlaoded ISO

---

### Post by krimzonstarr on 2010-09-05
Unfortunately, I have had this problem before. Most likely, your download of the iso is slightly corrupted. Make sure to check the md5sum on all your downloads. Instructions can be found at [https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

On a related note, torrent downloads verify the file integrity while downloading, so I find them MUCH more reliable. Good luck!

---

### Post by Guilden_NL on 2010-09-05
> **krimzonstarr said:**
> 

On a related note, torrent downloads verify the file integrity while downloading, so I find them MUCH more reliable. Good luck!

Yeow, my experience with Torrents has been sooo much different.  I find them to be like Napster circa 2000, lots of hit or miss.

As for my experience, give me a FTP download first, http second, torrents, bleh...

I agree with the assessment of a bad image, but in my experience of helping others out, most of the time it isn't the downloaded file being corrupted that's the cause, it's the ISO burning process.

---

### Post by krimzonstarr on 2010-09-05
> **Guilden_NL said:**
> Yeow, my experience with Torrents has been sooo much different.  I find them to be like Napster circa 2000, lots of hit or miss.

As for my experience, give me a FTP download first, http second, torrents, bleh...


I have yet to have successfully downloaded ANY iso with an intact md5sum on my wifi, except via torrent. Lots of network diversity out there, for such two widely different results!

---

### Post by Kyley on 2010-09-06
Fixed :D it was either an issue with the iso or the disk, I downloaded the torrent and staged he buring to my hard drive, clicked the verify box etc and its working, thanks for the help :)

---

### Post by krimzonstarr on 2010-09-06
> **Kyley said:**
> Fixed :D it was either an issue with the iso or the disk, I downloaded the torrent and staged he buring to my hard drive, clicked the verify box etc and its working, thanks for the help :)

Glad you got it working! Happy Ubuntu'ing!

---

### Post by baddnady23 on 2010-09-06
> **Kyley said:**
> when I can actually make it work I plan to do away with windows altogether


Backup your important documents and do it now!  :p

---

