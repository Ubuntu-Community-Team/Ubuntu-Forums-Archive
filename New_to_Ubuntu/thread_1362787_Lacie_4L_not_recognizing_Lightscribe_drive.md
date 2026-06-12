---
title: "Lacie 4L not recognizing Lightscribe drive"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by ricardisimo on 2009-12-23
I have the following multi-use CD/DVD drive:
```
*-cdrom:1
                description: DVD-RAM writer
                product: CDDVDW TS-H653R
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 0301
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
```
For some reason, 4L (the more advanced lightscribe utility for Linux) doesn't see it at all. The LightScribe SimpleLabeler does, however, although even that is somewhat hit or miss, and might even have something to do with the discs used... some colored blank discs, like the green ones, don't work as well as, say, the yellow or red ones.

I's weird and annoying, and this comp cost me a bundle, so it's particularly troublesome to have it be so persnickety. Is there any way to help 4L recognize the appropriate drive?

Thanks.

---

### Post by Geoff918 on 2009-12-23
You might want to try the hardware forum.

My guess would be that you're missing a driver somehow. The working program may have something already built-in to the code to make it recognize the card. I'll google for you and see what I might find.

EDIT:

This guy had a missing dependency:

[http://ubuntuforums.org/showthread.php?t=929976](http://ubuntuforums.org/showthread.php?t=929976)

FIGURED IT OUT:
 	Code:
 	sudo apt-get install libstdc++5 
and then you have to have gksudo to start it:
 	Code:
 	gksudo 4L-gui 
Some other drivers you might need:

[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

And one final link:

[http://onlyubuntu.blogspot.com/2008/05/howto-install-lightscribe-in-ubuntu.html](http://onlyubuntu.blogspot.com/2008/05/howto-install-lightscribe-in-ubuntu.html)

---

### Post by ricardisimo on 2009-12-23
Thanks for replying. I appear to have several packages in that family - libstdc - but all are ++6 and up. Are these the sort of libraries that might conflict? Can I safely install the ++5 variant without worry? Thanks again.

---

### Post by ricardisimo on 2009-12-23
Never mind. It's not even an option:
> libstdc++5:

Package libstdc++5 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
Sigh. In the Windows forums regarding similar issues, the solution appears to be "send it back to HP." Maybe I should just follow suit. Anyone else have the same problem?

---

### Post by amicable on 2010-02-14
I'm having the same problem. The aliened rpm from Lacie (LaCie LightScribe Labeler 1.0 Linux.rpm) does not work. The gui fires up but no drive can be selected.

Trying the command line, I get:

> sudo 4L-cli enumerate
Using /etc/lightscribe.rc
Segmentation fault


libstdc++5 (if this is the issue) can't be installed as it's been superceded; I have libstdc++6 installed on my Karmic.

The simple text labelling app works great with my Lightscribe.

The Lacie rpm can be difficult to find on the Lacie download site; [here's a link to the relevant download page.]("http://www.lacie.com/us/support/drivers/driver.htm?id=10061"). 

Anyone experience similar or has an idea for further diagnostics or a solution?

---

### Post by malrost on 2010-02-15
I also have this problem.

I'd had a problem-free LaCie application with 9.04. The upgrade to 9.10 borked it, and it remains borked.

---

### Post by amicable on 2010-02-16
I wonder if the rpm's are still working for users of other distros. It seems that the Lacie Linux Lightscribe drivers are pretty old. There must be a dependency somewhere that has failed but it's beyond my abilities to find out what, never mind suggest a fix.

---

### Post by ricardisimo on 2010-02-17
Do either of you dual-boot with Windows? I found a few threads elsewhere that suggested that this might be a hardware issue, and not OS or app. The easiest way to confirm or deny would be to check against XP/Vista/7, for which most of the software was originally intended.

---

### Post by amicable on 2010-02-17
Were the other threads recent? For malrost, this has only just appeared as an issue so it can't be hardware related if his unit was running as recently as Jaunty 9.04. 

Additionally, the Lacie Lightscribe functions perfectly with the text only functions, so there's nothing wrong with the laser burning and Karmic's ability to communicate with it at a low level. 

I don't run Windows; I bought my Lacie Lightscribe after installing Ubuntu Karmic 9.10. AFAICT it seems to be an issue with the Lacie 4L graphics software alone.

---

### Post by redbook4574 on 2010-02-17
> **amicable said:**
> Were the other threads recent? For malrost, this has only just appeared as an issue so it can't be hardware related if his unit was running as recently as Jaunty 9.04. 

Additionally, the Lacie Lightscribe functions perfectly with the text only functions, so there's nothing wrong with the laser burning and Karmic's ability to communicate with it at a low level. 

I don't run Windows; I bought my Lacie Lightscribe after installing Ubuntu Karmic 9.10. AFAICT it seems to be an issue with the Lacie 4L graphics software alone.

Seems to work fine on mine with an external lightscribe, i assume you have all the other stuff installed ie. simple lightscribe labler and the driver. One thing I have always found is to install in the order, driver - lightscribe simple and then lacie otherwise you will get problems.

---

### Post by redbook4574 on 2010-02-17
> **redbook4574 said:**
> Seems to work fine on mine with an external lightscribe, i assume you have all the other stuff installed ie. simple lightscribe labler and the driver. One thing I have always found is to install in the order, driver - lightscribe simple and then lacie otherwise you will get problems.


try this page for the relevant progs 

[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

---

### Post by amicable on 2010-02-17
Yes, as I mentioned, the simple labeller works great. 

I just tried a complete uninstall then install of 4L-gui via Synaptic but the Lightscribe drive still doesn't appear.

---

### Post by redbook4574 on 2010-02-17
> **amicable said:**
> Yes, as I mentioned, the simple labeller works great. 

I just tried a complete uninstall then install of 4L-gui via Synaptic but the Lightscribe drive still doesn't appear.

Forget synaptic try this for system software

[http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814](http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814)

Then this for lacie 4l

[http://www.lightscribe.com/downloadSection/linux/index.aspx?id=815](http://www.lightscribe.com/downloadSection/linux/index.aspx?id=815)

Hope it helps..

---

### Post by amicable on 2010-02-17
Hi redbook; Forgive me, but I think you miight be confusing the simple labeller with the full disc graphics 4L app. Your links to the two packages are the same apps that run perfectly for me already. There is no issue with these at all.

It is [the 4L software]("http://www.lacie.com/us/products/product.htm?pid=10803") that fails to work on Ubuntu 9.10.

I use Synaptic to search installed packages easily. The Lightscribe software can only be installed by debs as it isn't in the repos. The 4L software only exists in rpm form so you have to convert to a deb. That's probably where the issue is.

---

### Post by redbook4574 on 2010-02-18
> **amicable said:**
> Hi redbook; Forgive me, but I think you miight be confusing the simple labeller with the full disc graphics 4L app. Your links to the two packages are the same apps that run perfectly for me already. There is no issue with these at all.

It is [the 4L software]("http://www.lacie.com/us/products/product.htm?pid=10803") that fails to work on Ubuntu 9.10.

I use Synaptic to search installed packages easily. The Lightscribe software can only be installed by debs as it isn't in the repos. The 4L software only exists in rpm form so you have to convert to a deb. That's probably where the issue is.


A deb file does exist for 4L, if you look on my first link you will find it. It is what I use to install 4L-gui.

---

### Post by amicable on 2010-02-18
> **redbook4574 said:**
> A deb file does exist for 4L, if you look on my first link you will find it. It is what I use to install 4L-gui.

Odd. It's not what I see at all. Look at the included files in those debs. No 4L anywhere.

And there's a note below the download page:

> You will also need to install a labeling program such as the Simple Labeler or LaCie's 4L labeler.

Maybe they've removed it.

---

### Post by redbook4574 on 2010-02-18
> **amicable said:**
> Odd. It's not what I see at all. Look at the included files in those debs. No 4L anywhere.

And there's a note below the download page:



Maybe they've removed it.


My first link not the lightscribe software

[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

Then check option 4

---

### Post by amicable on 2010-02-18
ok. Unfortunately it's the same version I already have installed (1.0 r6); it doesn't work: no drive can be selected.

---

### Post by redbook4574 on 2010-02-18
Only suggestion I can make is to completely un-install all lightscribe software via synaptic - reboot, then try following the instructions on Ubuntu community it has always worked for me ever since 8.04. What have you got to loose??

---

### Post by amicable on 2010-02-18
> **redbook4574 said:**
> Only suggestion I can make is to completely un-install all lightscribe software via synaptic - reboot, then try following the instructions on Ubuntu community it has always worked for me ever since 8.04. What have you got to loose??

Indeed. I tried that already; still no joy  I'll go over it once again just in case I missed sthg. At least I'm clear now which packages you're talking about :)

---

### Post by malrost on 2010-05-01
Bumping this thread back up. I just upgraded to 10.04 and am still having the same problem: my drive is not recognized. I am able to use Lacie on a Fedora installation on this same box, and a different lightscribe app. on my XP installation.

[URL="http://ubuntuforums.org/showthread.php?t=1367690&highlight=lightscribe"]
This thread[/URL] suggested plugging the drive into a different SATA port; tried it and still doesn't recognize the drive.

---

