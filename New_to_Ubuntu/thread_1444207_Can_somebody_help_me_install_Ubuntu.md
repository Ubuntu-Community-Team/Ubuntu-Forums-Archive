---
title: "Can somebody help me install Ubuntu?"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by TigerEar on 2010-04-01
Hey guys, 

I was wondering if somebody could help me, I'll give you a bit of background to my situation.

I've used Windows all my life (I don't even know how to use a Mac really) and when I was in Japan a few months ago a computer I used there had Ubuntu on it. It seemed faster than the Windows one and looked better as well, and that's all I really care about - speed and looks.

Anyway, I'm not completely stupid with computers - and when I say computers I mean I know how to get things done in Windows - but I really don't know that much about installing another OS or disk partitions etc.

I decided to download and install Ubuntu as a second OS because my version of Windows 7 had been playing up for a while and I was sick of re-installing everything. I downloaded 9.10 and installed it but couldn't really figure out what to do so I let it sit there for a bit. 

Then my Windows 7 crashed big time and I had to do a system restore. Now, at my system boot, when I select Windows 7 it loads, but Ubuntu goes into this GRUB screen and when I type "boot" it says there isn't a kernel installed. I don't even know what a kernel is!

So basically I'm looking to somehow uninstall that Ubuntu and reinstall it so it works again, but I really, really have no idea how.

Sorry if this is really dumb, but can anybody help me? I'd love to get this working and maybe switch to it as my primary OS if I can get used to it

Thanks,

TigerEar

---

### Post by TheNerdAL on 2010-04-01
You can try going into safe mode(I forget what it's called. Correct me if I'm wrong anyone.)and clicking something that talks about fixing packages.

---

### Post by NightwishFan on 2010-04-01
Sure! Do you already have a partition available with Ubuntu? If not look to this guide for help:
[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)

Here is additional help on dualbooting:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you want to install Ubuntu as your only OS, back up your data onto a DVD or another computer and follow this guide:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://www.youtube.com/watch?v=w8a-smrPlvE&hd=1](http://www.youtube.com/watch?v=w8a-smrPlvE&hd=1)

Please ask if you have any other questions or need more personal help, I can assist you.

---

### Post by dsmskyline on 2010-04-01
I am having kind of similar issues as well. Is it ok to message you directly or would you rather I start a new thread?

---

### Post by NightwishFan on 2010-04-01
If you meant me, I would think staring a new thread would be better. I do not mind private messages, however leaving the solutions for others to find is always better.

---

### Post by dsmskyline on 2010-04-01
I was refering to you NightwishFan, I was having an issue with a clean install with no prior OS but it may be working. Ill make a new thread if need be.

---

### Post by NightwishFan on 2010-04-01
Please go ahead, and link me to it. I will respond there.

---

### Post by TigerEar on 2010-04-01
Thanks for the replies guys.

I just tried to shrink my main partition (I have two, one 10gb Dell Backup partition and my 136gb main drive) but Windows told me it couldn't because "it may be corrupted". I ran chkdsk and there was no change.

Do I have to do a clean install of Windows? Again?

Cheers,

TigerEar

---

### Post by NightwishFan on 2010-04-01
You need to run chkdisk and defragment it first, that is a must. Are you using the partitioner built into Windows? If not then use that one, it is found by right clicking My Computer and clicking "Manage".

---

### Post by TigerEar on 2010-04-01
Yeah I'm using that one, I'll defrag and then try again

---

### Post by TigerEar on 2010-04-01
Okay, I think we have made some progress.

I defragged, then ran chkdsk, and now my C drive displays 89gig free, which is roughly the ammount I had before I installed 16 gigs worth of Ubuntu give or take.

I noticed there was a file in my C drive that was labelled Ubuntu - when I went in there there was an Uninstaller. I ran that, it asked me if I wanted to uninstall Ubuntu and I accepted. I then rebooted, but still get presented with the option of booting up either Windows 7 or Ubuntu even though Ubuntu doesn't actually exist anymore.

Where to from here friends?

---

### Post by NightwishFan on 2010-04-01
Ah you installed using Wubi! That does not cause any partitioning of the drive. It is not really a "true" install of Linux but it has much of the characteristics of one. Are you attempting a normal install or does the concept of Wubi seem more to your liking? If you need any clarification please ask. Read (a tiny bit as the second one is long) this FAQ and Wiki article on the subject.
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I will sum it up:
> Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way. 

To remove from the boot menu:
> In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via Control Panel > System > Advanced > Startup and Recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys and remove the Wubi block.

---

### Post by TigerEar on 2010-04-01
Ah okay that's easier. So to do a "true" install of ubuntu I need to create a partition and theeeen... I dunno?

---

### Post by NightwishFan on 2010-04-01
You need to download and burn the Ubuntu live/install cd. Ensure the partition you make for Ubuntu is just empty space, not NTFS. Ubuntu does not use the Windows filesystems. Like so:
[[WINDOWS NTFS] EMPTY SPACE]

I would ensure Ubuntu works with your hardware before installing. Download the CD here. It can actually boot from the CD without installing or changing Windows. It is like a test mode, and if all your hardware works the install process is simple. You can even browse the web while installing. For now, start here by downloading the Ubuntu ISO. If you have already done that skip ahead.
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

How to burn:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Now you have Ubuntu downloaded and burned, place the CD in your drive and reboot. If you machine is set to boot from CD you should get an Ubuntu menu. Select "Check for errors". If the CD has errors you need to burn a new CD at a slower speed. If there are no errors, reboot and select: "Try Ubuntu Without Changing Your Computer"

Play around with Ubuntu on there. It will be much slower than a real installation as it is on a CD. If you find problems, ask us here. If you like it, click Install Ubuntu on the desktop and follow the process here to install. All of this is not as hard as it sounds.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by TigerEar on 2010-04-01
Cool! Thanks for your help. I'll give it a go tonight and let you know how I get on in a few days.

Cheers man

---

### Post by TigerEar on 2010-04-01
You were right, it really was easy after I got a little bit of help.

I installed the 10.04 beta because I figured the full version will be out soon and there's no point learning 9.10 only to have to change some stuff. I'm taking things slow - I installed my graphics card driver and Google Chrome and everything's going well so far. 

I need help with two little things though - somehow I accidently deleted the bluetooth icon and battery icon from the top panel. I tried re-adding the notification area but nothing happens, can anyone help?

Also, something that really, really bugs me - its not a huge issue but I'm a bit OCD with this kinda stuff - is that to the left and right of my desktop wallpaper there's a small, one pixel wide frame that *sometimes* disappears but most of the time is there. Can I get rid of this? it drives me nuts!

Thanks again for all your help,

Satisfied Tiger Ear

---

### Post by NightwishFan on 2010-04-01
You should not have started Ubuntu using a beta I think. The "new versions" at not usually so different. Run an update from System -> Administration -> Update Manager. It will be a LOT of updates. That will fix your issue.

Please note the beta is sometimes in a strange state because of all the debugging and experimenting the developers are doing. It is not for production use until it's release late april and some would argue to wait a month.

As for the bluetooth issue, you need the notification area or the indicator applet. If you want, run this command to reset the panel to default. Press alt+f2, paste this, and hit enter. 
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel
```

If the panel does not re-appear press alt+f2 and run this:
```
killall gnome-panel
```

If nothing reappears, save your work and then press: alt+prntscrn+k

---

