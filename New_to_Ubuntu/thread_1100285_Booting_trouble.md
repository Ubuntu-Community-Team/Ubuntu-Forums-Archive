---
title: "Booting trouble"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by dhirajkhanna on 2009-03-19
I am trying in vain to install Kubuntu (Intrepid) on my Dad's desktop and need urgent help to save some face!!
Everything is fine till the splash screen. It seems to take like forever ans still doesn't boot. Doesn't really freeze as the mouse cursor still moves, but nothing happens. I have done a reinstall too but no joy. I am able to do a console login but startx gives the same result. Could it be a graphics card issue?
I need urgent help to convert a die-hard xp fan to linux and unfortunately, the start hasn't been to smooth!!

---

### Post by anewguy on 2009-03-19
Since you can log in to a terminal session, Ubuntu is obviously running.  Starting X and getting a blank screen is usually indicative of needing a driver for the video card.  So, log in to a terminal session, do the following, and post the output back here:

lshw -C network

lspci

If it's a laptop, also do the following:

lsusb



Dave :)

---

### Post by bryanergy on 2009-03-19
> **dhirajkhanna said:**
> I am trying in vain to install Kubuntu (Intrepid) on my Dad's desktop and need urgent help to save some face!!
Everything is fine till the splash screen. It seems to take like forever ans still doesn't boot. Doesn't really freeze as the mouse cursor still moves, but nothing happens. I have done a reinstall too but no joy. I am able to do a console login but startx gives the same result. Could it be a graphics card issue?
I need urgent help to convert a die-hard xp fan to linux and unfortunately, the start hasn't been to smooth!!

Was this a live or CD install?

If your system has a network card, and is plugged into a system that won't assign an IP address, it may be sending out DHCP requests for a while before giving up. If you have an unrecognized USB device plugged in, it may take extra time to give up on it. I found out my external USB hub sometimes works fine, but with two of my USB drives, it really slows the entire system down to a crawl. So I replaced it and back to full speed.

If you do have Internet connection set up correctly (ping ubuntuforums.com works, then use the console to vi the /etc/apt/sources.list to disable or replace the CD entries with [k]ubuntu repository including stable/main and contrib and non-free; the contrib / non-free may be needed for nvidia or Intel video driver.

Then do "sudo apt-get update" which will update the list of packages, though it doesn't actually install anything new. Then you can "sudo aptitude" and look for packages that affect the display, or simply update everything - I have added, surprisingly, hundreds of megs of updates since installing [Ubuntu] 8.10. On my earlier sarge->etch->lenny (with KDE) installs, I broke the display several times (over the past three years) by doing insufficient updates, then went back and hit + in aptitude interface, or small u to update package list, then capital-U which updates everything, and then hit g and then for broken packages, usually hit B to find the next one, sometimes simply hit - on the obsolete packages, or + on new dependencies, until the red, broken, all go away, then g (first g shows what will get installed, make sure there's no red / broken left, and then hit g again) and let the hundreds of megs come in, then reboot and startx works again.

If you know you have nvidia hardware, you can install thus:
sudo apt-get install nvidia-xconfig
This will pull in a bunch of packages
Then from root, type nvidia-xconfig; it will backup your current /etc/X11/xorg.conf and add the needed fields
I'm less familiar with Intel but recently set that up on a Debian-etch or lenny and in that case had to read docs or example xorg.conf and then manually edit my xorg.conf to add the lines, device simply "Intel", I think. This cleaned up my HD video playing.

On lsusb there is a -v option that gives much more detail, though it takes some effort to make sense of the extra detail. For example, if the root hub has four interfaces, you will see extra info about the interface replicated for each interface, even if nothing is live on the interface. However there may be extra useful info for whatever is actually connected.

---

### Post by dhirajkhanna on 2009-03-19
This was a CD installation on a desktop and the same CD was used for successfully installing on a laptop. The output of lsusb is as follows:-
Bus 004 Device 002: ID 0c45:6270 Microdia U-CAM PC Camera NE878
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1d6b:0001 Linux Foundation 1.1 root hub

There was a modem(SmartAX MT882) connected to the USB port and I disconnected it as it didn't have a linux driver. However after that too, the problem remains. From the command line, on typing sudo startx, the system tries to boot. I get the symbols for KDE 4.1, but after the third symbol, the system remains inactive. Doesn't hang, but doesn't progress any further too.
Help would be appreciated.

---

### Post by anewguy on 2009-03-19
Sorry about my previous post - instead of the lshw -C network (I was working on multiple posts at the same time), please post the output of:

lspci

That way we can see what your adapter is.  When this happens on a fresh install or upgrade, it's usually a video driver issue.  Once we have the above, we can proceed on to trying to get a driver to work for you.

Dave :)

---

### Post by rhcm123 on 2009-03-19
Also, would you mind posting your specs? It might be simply the fact that your PC does not have the power to run KDE (KDE sucks up resources by a metaphor i'm going to stop right... now.) :)

---

### Post by dhirajkhanna on 2009-03-20
The result of lspci for my video adapter is 
00:02.0 VGA compatible controller : Intel Corporation 82845G/GL[Brockdale-G]/GE Chipset Integrated Graphics Device (rev 01)

Do you think installing ubuntu instead of kubuntu will solve the problem?

---

### Post by anewguy on 2009-03-21
I seem to remember this is the integrated graphics processor 845.  Try logging in to a terminal session and doing the following:

sudo apt-get remove compiz
sudo apt-get remove compiz-core

Then reboot and see what happens.  I have seen this listed as the solution for other people using the 845 IGP as apparently it doesn't cooperate with compiz.

Let us know what happens.

Dave :)

---

### Post by ivanvajar on 2009-03-21
Intel Corporation 82845G/GL[Brockdale-G]/GE Chipset Integrated Graphics Device made me some trouble also. Disabling Compiz is a good idea, but I don't think it will make any difference. If graphics processor doesn't support Compiz, Compiz will just not start at all. If you have internet connection, boot into terminal and type:

> sudo apt-get update && sudo apt-get install xserver-xorg-video-intel

---

### Post by dhirajkhanna on 2009-03-21
Thanks a lot guys! Removing compiz and compiz-core solved it for me. Incidentally, I had already switched over to ubuntu rather than the resource hungry kubuntu. However, I feel that removing compiz in kubuntu would also have solved it. 
Thanks nonetheless.
Cheers

---

### Post by rhcm123 on 2009-03-21
> **dhirajkhanna said:**
> Thanks a lot guys! Removing compiz and compiz-core solved it for me. Incidentally, I had already switched over to ubuntu rather than the resource hungry kubuntu. However, I feel that removing compiz in kubuntu would also have solved it. 
Thanks nonetheless.
Cheers

yeah, integrated graphics cards usually don't have the power for KDE

---

### Post by dhirajkhanna on 2009-04-19
Sorry guys, I am back.

I am facing the same problem on a desktop installation of kubuntu. The graphics card is also the same (rev 03). However, this time removing compiz did not help. In fact apparently, compiz is not installed.

Also how do i configure my network connection through the console?

Thanks in advance

---

