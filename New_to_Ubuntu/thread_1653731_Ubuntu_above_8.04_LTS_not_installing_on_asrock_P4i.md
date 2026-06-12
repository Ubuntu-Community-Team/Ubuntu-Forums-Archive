---
title: "Ubuntu above 8.04 LTS not installing on asrock P4i45 GV chipset."
date: 2010-12-27
forum: New to Ubuntu
---

### Post by John Galt on 2010-12-27
Hi,

my system configuration is as follows:

asrock P4i45 GV chipset (845 GV) with an AGP 8X slot for graphic support 
nvidia geforce 4 MX 4000 graphics card (128 mb)
Pentium 4 processor (2.4 Ghz)
512 MB ram
80+40 GB samsung hard drives.
Samsung DVD-R\CD-RW combo drive


As you try to boot from the installation media; you are able to see the start up screen which- after letting you select the installation language; gives you option to try ubutu or to check the media for defects among others. Upon selecting the option to check the media (CD or DVD; i tried both) for defect; the cursor blinks on top of the empty screen and then four to five pages of program errors wildly scroll up. When the screen finally stops the only thing I am able to understand are phrases like "Kernel panic", "attempting to kill init!" etc.

This issue has been observed not only with Ubuntu 10.04 but also with Ubuntu 10.10. 
Though I am confident that the installation media is good;how do you proceed from this stage?

I have installed Ubuntu 8.04 LTS and it works pretty well. Had issues with nvidia proprietary drivers. At that time I did not want to access internet through linux as I had no idea how to setup an internet connection. (Had installed it just for "fun".) So downloaded the driver on the win xp platform and then heeding to the good community's advise. Please refer to my earlier posts for further details.

My guess is that Ubuntu recognizes both the onboard graphics solutions and the GPU. There is also no option in the bios to disable to onboard graphics and let the nvidia card take over so that Ubuntu recognises it only. In another of my previous attempts to find an answer, as this issue was faced by another distro user (mepis, the details are available in last sections of a previous thread and a link, which again will be provided at the end), he had found a way to make it work by blacklisting something. That is he used some high level technique or something of which i am unaware as I have no programming experience. I am a casual desktop user with limited computer capabilities (read average joe; so please any solution is requested in a manner like step one, then step two.... it will help and will be respected)  

The link of forum where the same problem is discussed - "http://mepislovers.org/forums/archive/index.php/t-6487.html".

Some Google, wiki and Ubuntu video tutorial later; I find that I would want to switch over to this OS asap.

Please help.

---

### Post by cariboo on 2010-12-27
Try setting **nomodeset**, before you boot from the Live Cd. Once at the menu, press F6 and use the arrow keys to select **nomodest**, press esc then press enter. You'll be able to boot into safe graphics mode.

---

### Post by John Galt on 2010-12-28
Hi,

did try your method just now.

Same result with the f6 option nomodeset. Pages scroll up fast and the last page shows the error - kernel panic - "not syncing : attempting to kill init!" And then there are lines and lines of zeros and programming stuff.

Now what.....?

---

### Post by Zill on 2010-12-29
> **John Galt said:**
> ...Though I am confident that the installation media is good;how do you proceed from this stage?..
I suggest you try your CD in a *different* PC to verify this.

If the "Check disk for defects" utility fails and/or the CD cannot run the OS "Live" then the disk is a dud!

---

### Post by Zill on 2010-12-29
John Galt:  Assuming you have verified your CD is good as I suggested in post [#4]("http://ubuntuforums.org/showpost.php?p=10291745&postcount=4"), the following link may be of interest...

[Ubuntu Linux’s kernel panic freeze with an Asrock motherboard and an NVidia gfx card]("http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/")

This *may* be related to your problem and explains how to disable the NVidia card *temporarily* and use the integrated video while Ubuntu is installed.  When Ubuntu has been properly installed, with the monitor connected to the integrated VGA output, it should be possible to blacklist the intel_agp driver as detailed in the link.  Note that this is an old link and things have changed slightly with the "blacklist" file now replaced by "blacklist.conf".  Just change the line in step 3 from 
```
sudo nano /etc/modprobe.d/blacklist
```
to
```
sudo nano /etc/modprobe.d/blacklist.conf
```
and in step 4 from
```
sudo gedit /etc/modprobe.d/blacklist
```
to
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
With the blacklist.conf file updated as described, reboot the PC with the monitor connected to the NVidia card.  Then open the System, Administration, Hardware Drivers menu and select the recommended driver in the usual way.  The NVidia driver should install and the PC can then be rebooted into your new OS.

Note that it is necessary for the PC to be connected to the internet, preferably via a wired connection, to ensure that the necessary drivers can be downloaded and installed when required.  Wireless drivers etc can be configured later if necessary.

---

### Post by Zill on 2010-12-29
Duplicate post

---

### Post by John Galt on 2011-01-01
Thank you, thank you and thank you again Mr. Zill.

I finally got my system up and running. Your link and the subsequent information did the trick.

Thank you again.

:p:p:p:p:p:p:p\\:D/

I am posting this message from Ubuntu 10.10 system. 

My first reaction - WOW and nothing short of it. Linux has exceeded my expectations and more. I do not even need drivers for my graphic card and adsl router. It has come bundled with everything. Linux is great.

However, how do you enable shockwave, flash and java?

In a tutorial, I was advised to use easy ubuntu or automatix. Which of the two is good? Are there any other options better than the other two?

Please advise.....and again....keep up the good work.

---

### Post by Zill on 2011-01-01
> **John Galt said:**
> ...I am posting this message from Ubuntu 10.10 system. 

My first reaction - WOW and nothing short of it. Linux has exceeded my expectations and more. I do not even need drivers for my graphic card and adsl router. It has come bundled with everything. Linux is great.

However, how do you enable shockwave, flash and java?

In a tutorial, I was advised to use easy ubuntu or automatix. Which of the two is good? Are there any other options better than the other two?...
Congratulations on getting your new system up and running :-)

As you have found, many things in Ubuntu "just work" but *sometimes* a little extra work is required.

Flash and Java are not enabled by default in Ubuntu in order to comply with the FOSS philosophy.  It is, however, easy to install this functionality, along with several other "desirable" features, with a single command:
```
sudo apt-get install ubuntu-restricted-extras

```
You can, of course, use the Synaptic Package Manager GUI to install this package if you prefer this to the terminal command.

"Easy Ubuntu" and "Automatix" are, I believe, now deprecated and the functionality they provided is now generally available directly from Ubuntu packages, rather than using these custom scripts.

AIUI Shockwave (a proprietary format) does not currently have Linux support.

---

### Post by John Galt on 2011-01-05
Thanks Mr Zill, for al the help. I have a perfectly fine Ubuntu system now and very very pleased with the way it works. If in the future I would want to shift from this distro, it would be only to increase my linux knowledge. Good bye XP, hello Linux.

P.S. Marking this thread as solved. :)

---

