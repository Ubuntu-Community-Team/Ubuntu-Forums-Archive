---
title: "Instaled 10.4 from windows 7 and almost nothing works"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by dreadshroud on 2010-09-12
Hi
My laptop is a Sony VPCCW26FA

I've tried installing ubuntu10.4 using wubi but I got a black screen without the flashing white dash
after searching the forums I've found a fix for that which was pressing e at the first option of the bootloader and replacing "quiet splash" with nomodeset

it worked and I finished installation/started working with it
however the graphics/reslution is very bad

I then tried updating my drivers (nvidia) and it insaled on the computer without a hasle

however when I try to open Nvidia X server settings it tells me
"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
I've searched all day for this fix and I've tried a few of the suggested ones but none worked

I've tried downloading different drivers, something involving ppa, reinstaling,disableing/enabling it again/restating a lot

When I open Hardware drivers, it tells me the driver is currently in use
If I disable the driver, my screen goes blank and I have to use "nomodeset" fix to get it starting

when other drivers are used ubuntu loads in low graphic mode and I can not log in without restarting

I instaled ubuntu 10.4 on another laptop and it works perfectly on there so I don't think I have a corrupted disk

---

### Post by philinux on 2010-09-12
I can only suggest trying the livecd on this machine.

---

### Post by dreadshroud on 2010-09-12
I got the wireless working and most of the stuff went right after that (reinstalled the drivers, toutchpad works,etc forums are very helpful)

but my graphics problem is still there, and I still get the nvidia driver not in use error that 
I mentioned above


only issues I have other than that is the brightness is not adjustable


what should I do with the live cd?

---

### Post by amjjawad on 2010-09-12
> **dreadshroud said:**
> Hi
My laptop is a Sony VPCCW26FA

I've tried installing ubuntu10.4 using wubi but I got a black screen without the flashing white dash
after searching the forums I've found a fix for that which was pressing e  at the first option of the bootloader and replacing "quiet splash" with  nomodeset

it worked and I finished installation/started working with it
however the graphics/reslution is very bad

I then tried updating my drivers (nvidia) and it insaled on the computer without a hasle

however when I try to open Nvidia X server settings it tells me
"You do not appear to be using the NVIDIA X driver.  Please edit your X  configuration file (just run `nvidia-xconfig` as root), and restart the X  server."
I've searched all day for this fix and I've tried a few of the suggested ones but none worked

I've tried downloading different drivers, something involving ppa, reinstaling,disableing/enabling it again/restating a lot

When I open Hardware drivers, it tells me the driver is currently in use
If I disable the driver, my screen goes blank and I have to use "nomodeset" fix to get it starting

when other drivers are used ubuntu loads in low graphic mode and I can not log in without restarting

I instaled ubuntu 10.4 on another laptop and it works perfectly on there so I don't think I have a corrupted disk

Hi there,
I'm not an expert but from all what happened with me and from all what  I've read over here, I might be able to help you a little bit.

First thing first, as Pilinux suggested, try to use the Live CD:
1- Insert your CD/DVD into your driver
2- Restart
3- Choose "Try" and don't install anything.

If the same issues will happen, then I guess you need the drivers.

I would suggest one more thing. Don't use Wubi as many wrote in the forum that it causes some issues. Try to boot from Ubuntu's CD and follow the steps. On Step 4, choose the 2nd option "Delete and use the entire disk" if and only if you have two Hard Disks. If you have only one, then I assume you already have two partitions on your primary HDD. It's better to have two partitions, one for Windows and the other for Ubuntu.
Of course, you need to remove/uninstall your current setup and start new one.

I'm not sure if you have two HDDs or not and honestly didn't check your signature but again, you still can boot from your CD and install the first option "Side by side" but I strongly recommend to have two partitions in case of 1 HDD.

Hope that would help and sorry if I wasn't great support to you!

---

### Post by dreadshroud on 2010-09-12
sorry I said I tried to instal with wubi but after It didn't work I instaled it form a cd
side by side with windows

should I still continue trying your suggestion?

thanks for your time

---

### Post by wilee-nilee on 2010-09-12
> **amjjawad said:**
> Hi there,
I'm not an expert but from all what happened with me and from all what  I've read over here, I might be able to help you a little bit.

First thing first, as Pilinux suggested, try to use the Live CD:
1- Insert your CD/DVD into your driver
2- Restart
3- Choose "Try" and don't install anything.

If the same issues will happen, then I guess you need the drivers.

I would suggest one more thing. Don't use Wubi as many wrote in the forum that it causes some issues. Try to boot from Ubuntu's CD and follow the steps. On Step 4, choose the 2nd option "Delete and use the entire disk" if and only if you have two Hard Disks. If you have only one, then I assume you already have two partitions on your primary HDD. It's better to have two partitions, one for Windows and the other for Ubuntu.
Of course, you need to remove/uninstall your current setup and start new one.

I'm not sure if you have two HDDs or not and honestly didn't check your signature but again, you still can **boot from your CD and install the first option "Side by side"** but I strongly recommend to have two partitions in case of 1 HDD.

Hope that would help and sorry if I wasn't great support to you!

Good stuff, I highlighted the part though that is not recommended with a Windows 7 install. You should shrink the W7 partitions with it's own disk manager it works great.

You can actually use gparted to shrink W7 but you have to untick the round to cylinders.

Any partition resizing in windows should be followed with a reboot to it to make sure it's working, then you install Ubuntu by booting the live cd.

---

### Post by amjjawad on 2010-09-12
> **dreadshroud said:**
> what should I do with the live cd?

The advantage of using the Live CD is to test Ubuntu on your machine before you install it. In your case, you already installed it. I guess it's better to go for my 2nd suggestion (remove your current installation of Ubuntu and use the Live CD to "TRY" Ubuntu first then "Install" it. You can access the Internet while you're on TRY so don't worry about drivers, I hope you could find the right one.

I just replied your first post so you can refer back to my previous reply!

---

### Post by uRock on 2010-09-12
> **dreadshroud said:**
> sorry I said I tried to instal with wubi but after It didn't work I instaled it form a cd
side by side with windows

should I still continue trying your suggestion?

thanks for your time
No, if you have installed in a partition, then wubi would be a step backwards at this point.

uRock

---

### Post by amjjawad on 2010-09-12
> **dreadshroud said:**
> sorry I said I tried to instal with wubi but after It didn't work I instaled it form a cd
side by side with windows

should I still continue trying your suggestion?

thanks for your time

Before anything, I would be a better support if I could know how many Hard Disks do you have?

---

### Post by amjjawad on 2010-09-12
> **wilee-nilee said:**
> Good stuff, I highlighted the part though that is not recommended with a Windows 7 install. [COLOR=Black]**You should shrink the W7 partitions with it's own disk manager it works great.**[/COLOR]

You can actually use gparted to shrink W7 but you have to untick the round to cylinders.

[COLOR=Red]**Any partition resizing in windows should be followed with a reboot to it to make sure it's working, then you install Ubuntu by booting the live cd**[/COLOR].

I loved the highlighted part in red. Yes, as long as Windows is unstable, that step is a must in my opinion.

The highlighted part in Bold is something I missed. Yes, it's much better to do that using Windows Disc Manager but it would be much more better to install Ubuntu on another HDD but that of course if he has 2 :)

---

### Post by wilee-nilee on 2010-09-12
> **dreadshroud said:**
> sorry I said I tried to instal with wubi but after It didn't work I instaled it form a cd
side by side with windows

should I still continue trying your suggestion?

thanks for your time

Are both Ubuntu and windows booting. With a side by side if W7 is going to work it should run a auto chkdsk, if it doesn't and can't boot this may be needed.

---

### Post by beew on 2010-09-12
Neither am I an expert but I don't think you can install graphic drivers with wubi, it is not a real installation, just a little play pen living as a folder inside windows so it is kind of limited and fragile.

A live cd cannot be written on so that is probably useless and it is also very slow, a better option would be a liveusb with persistence, but I don't think you can install things like Nvidia drivers in the liveus because it involves some changes in the kernel and it will break the live usb, at least with Lucid I killed my live usb everytime I tried.

So without taking the risk of dual booting (this way doesn't install anything in  your PC) the only option left appears to be a full installation into an external drive and then plug it in your pc to try to install drivers. That is how I tested whether I could install Nvidia driver in Lucid, I did it with a full install in an 8 g pendrive.

Here is how I did it [http://ubuntuforums.org/showthread.php?t=1536330](http://ubuntuforums.org/showthread.php?t=1536330)
Now of course you need to boot from a live cd or a live usb in order to do an installation on the targeted usb, so you'll need either a live cd plus a usb or  a live usb and a usb into which you want to install Ubuntu.

---

### Post by dreadshroud on 2010-09-12
I'm sorry but I don't know what a partition is :confused:

I'm no expert but don't think I need to reinstall ubuntu again, becuase scince the morning I got most of my laptop working except for the graphics 
the relution is still horrible and I can not change my monitor settings 

and I know it's not becuase my graphics card is bad, I could play high graphic games like dragons age on ultra high without any lag


this is the error I am getting (hope pic is not too big)[IMG]http://img534.imageshack.us/img534/6913/screenshotdre.png[/IMG]

---

### Post by wilee-nilee on 2010-09-12
> **amjjawad said:**
> I loved the highlighted part in red. Yes, as long as Windows is unstable, that step is a must in my opinion.

The highlighted part in Bold is something I missed. Yes, it's much better to do that using Windows Disc Manager but it would be much more better to install Ubuntu on another HDD but that of course if he has 2 :)

I have used the disk manager and gparted, but I have the install DVD and can boot it as last resort to set up a chkdsk if needed. Actually chkdsk should be run with regularity in a Windows setup depending on use.

---

### Post by uRock on 2010-09-12
After installing the nvidia driver, did your restart? If not, then that is all that will be needed.

---

### Post by dreadshroud on 2010-09-12
> **wilee-nilee said:**
> Are both Ubuntu and windows booting. With a side by side if W7 is going to work it should run a auto chkdsk, if it doesn't and can't boot this may be needed.

yes, I'm currently running them side by side

windows did run a disk check by itself yesterday (right after instaling unbuntu)

I'm assuming its auto chkdsk? becuase it wasn't a program inside windows it checked when I booted windows for the first time after instaling linux

---

### Post by dreadshroud on 2010-09-12
> **uRock said:**
> After installing the nvidia driver, did your restart? If not, then that is all that will be needed.

yes I did restart after instaling drivers
all other hardware worked fine but I am still getting same error as shown in picture above


sorry for taking your time everyone, many thanks

---

### Post by amjjawad on 2010-09-12
> **dreadshroud said:**
> I'm sorry but I don't know what a partition is :confused:

I'm no expert but don't think I need to reinstall ubuntu again, becuase scince the morning I got most of my laptop working except for the graphics 
the relution is still horrible and I can not change my monitor settings 

and I know it's not becuase my graphics card is bad, I could play high graphic games like dragons age on ultra high without any lag


this is the error I am getting (hope pic is not too big)

1- When you're on Windows. Go to My Computer and check how many letters do you have? from the icon you could tell whether it's a Hard Disk or a DVD Drive, etc.

2- 
A- Right Click on My Computer
B- Manage
C- Disc Management (I don't have Windows now so hope it's the correct name)
D- Check how many "DISC/DISK" do you have? that would tell you how many Hard Disk Drivers do you have

3- I suggested to re-install Ubuntu just in case something was wrong during the installation. I've been suffering for 3 days with a much more complicated problem than yours and finally I got Ubuntu working

4- From my little experience, it's highly recommended to install Ubuntu on a separate partition or another Hard Disc if you have two.

5- A partition is: [http://www.tech-faq.com/hard-disk-partition.html](http://www.tech-faq.com/hard-disk-partition.html)

---

### Post by beew on 2010-09-12
I think in order for the Nvidia drivers to work you have to disable/kill/remove the default noveau drivers first.  There are some threads about it and I have them bookmarked but it is on another computer which I have no access to right now. I installed my Nvidia driver from this ppa:

  **ppa:ubuntu-x-swat/x-updates**

(I don't know if you need to kill your noveau drivers if you install from this ppa, I couldn't kill mine because they seemed to regenerate and I never got the screen with only command prompt as they said it would happen in the  forum threads. So after a few attempts I installed from the PPA and it worked, I have no idea whether the noveau drivers were dead before the installation[B])
[/B]

---

### Post by amjjawad on 2010-09-12
> **dreadshroud said:**
> yes I did restart after instaling drivers
all other hardware worked fine but I am still getting same error as shown in picture above


sorry for taking your time everyone, many thanks


You're not taking our time, we'd love to help so don't be sorry :)

Hope you don't mind my question but when you say there's a problem with the resolution (forget the error msg now), what do you mean? because as far as I can tell from your screen shot that you attached, everything is fine. Not sure though if the background picture is in B&W or not but as far as I can see the panel and icons, above all, the screen shot itself is very clear and has no problem, I could assume that everything is fine. So, what do you mean? do you have another screen shot that could show what's wrong with the resolution?
Again, forget the error msg right now :) I just want to understand what do you mean by bad resolution!

---

### Post by beew on 2010-09-12
Just right click anywhere on the screen and go to change background and try to enable extra visual effects then you will know whether you have the Nvidia driver installed.

---

### Post by amjjawad on 2010-09-12
> **beew said:**
> A live cd cannot be written on so that is probably useless and it is also very slow, a better option would be a liveusb with persistence, but I don't think you can install things like Nvidia drivers in the liveus because it involves some changes in the kernel and it will break the live usb, at least with Lucid I killed my live usb everytime I tried.

So without taking the risk of dual booting (this way doesn't install anything in  your PC) the only option left appears to be a full installation into an external drive and then plug it in your pc to try to install drivers. That is how I tested whether I could install Nvidia driver in Lucid, I did it with a full install in an 8 g pendrive.

Here is how I did it [http://ubuntuforums.org/showthread.php?t=1536330](http://ubuntuforums.org/showthread.php?t=1536330)
Now of course you need to boot from a live cd or a live usb in order to do an installation on the targeted usb, so you'll need either a live cd plus a usb or  a live usb and a usb into which you want to install Ubuntu.

He doesn't need to write on the Live CD, he needs it to try Ubuntu before installing it but it's a bit too late now as long as he installed it already.

Yes, USB is much faster and I just installed Ubuntu today using an USB stick.

Why he needs to save the drivers on USB anyway? if he could find the right/correct updates for his Video Card, then he could just download it, right?

 "So without taking the risk of dual booting (this way doesn't install  anything in  your PC) the only option left appears to be a full  installation into an external drive and then plug it in your pc to try  to install drivers." << why all that hassle? you could have done it in much easier way!
In my opinion, that's unnecessary hassle but that's only me!

:)

---

### Post by dreadshroud on 2010-09-12
> **amjjawad said:**
> You're not taking our time, we'd love to help so don't be sorry :)

Hope you don't mind my question but when you say there's a problem with the resolution (forget the error msg now), what do you mean? because as far as I can tell from your screen shot that you attached, everything is fine. Not sure though if the background picture is in B&W or not but as far as I can see the panel and icons, above all, the screen shot itself is very clear and has no problem, I could assume that everything is fine. So, what do you mean? do you have another screen shot that could show what's wrong with the resolution?
Again, forget the error msg right now :) I just want to understand what do you mean by bad resolution!


I wish my screen looked half as good as the screenshot (looking at it in windows)
it looks horrible in Ubuntu

---

### Post by dreadshroud on 2010-09-12
> **beew said:**
> Just right click anywhere on the screen and go to change background and try to enable extra visual effects then you will know whether you have the Nvidia driver installed.

can't enable them
but in system->Adminstration->Hardware drivers it says it's instaled and currently in use

---

### Post by amjjawad on 2010-09-12
> **dreadshroud said:**
> can't enable them
but in system->Adminstration->Hardware drivers it says it's instaled and currently in use

Is it possible for you to uninstall or remove the driver?

If you could do that, remove it, restart your laptop then re-install "the driver" again and of course restart your laptop once more.

---

### Post by dreadshroud on 2010-09-12
> **amjjawad said:**
> Is it possible for you to uninstall or remove the driver?

If you could do that, remove it, restart your laptop then re-install "the driver" again and of course restart your laptop once more.

I've tried doing that but it opens up in low graphic mode and then I select autoconfigure option and it loads fine but graphics are still bad looking

regardless I'll try again

[IMG]http://img707.imageshack.us/img707/1250/55535429.png[/IMG]
I think I have two partitions? or three?

---

### Post by amjjawad on 2010-09-12
> **dreadshroud said:**
> I've tried doing that but it opens up in low graphic mode and then I select autoconfigure option and it loads fine but graphics are still bad looking

regardless I'll try again


I think I have two partitions? or three?


My bad, I keep forgetting you have a laptop which came with ONLY one Hard Disk.

You have only 1 partition for Windows (C:) and 3 for Ubuntu but you can't access these partitions using Windows, they're reserved for Ubuntu. In fact, the filing system is quite different.

If you really want to avoid lots of hassle now and in future, I still strongly recommended to uninstall this copy of Ubuntu and install new one. Also, you need to create two partitions using Disc Management. I can teach you how to do it even without looking at your screen shot :) don't worry about the 3 partitions, you can get them back after you remove Ubuntu and yes, I can tell you how to do so.

Now, it's your call. 
You might solve this problem now (graphics) but you'll face more problems in the future either from Windows or Ubuntu.

---

### Post by amjjawad on 2010-09-12
Wait, are you accessing/using Ubuntu from Windows? I'm sure I read that when you said you used Wubi but it didn't work so you installed it again. I could only understand you used Wubi again, otherwise how come you can access Ubuntu from Windows? I'm just confused now :o

---

### Post by beew on 2010-09-12
> He doesn't need to write on the Live CD, he needs it to try Ubuntu before installing He wanted to try whether he could install the Nvidia driver, where would he install it if he couldn't write on the medium? Anyway I found the live CD a horrible way to try Ubuntu because it is so painfully slow, not to mention that you have to store the CDs. Creating a live usb from iso is a lot faster and cleaner  than burning a CD, so if one has some usb sticks lying about and can boot from usb there is absolutely no reason to use a live CD though people keep giving out that advice as default. :)

---

### Post by dreadshroud on 2010-09-12
> **amjjawad said:**
> Wait, are you accessing/using Ubuntu from Windows? I'm sure I read that when you said you used Wubi but it didn't work so you installed it again. I could only understand you used Wubi again, otherwise how come you can access Ubuntu from Windows? I'm just confused now :o

it didn't work when I instaled with wubi
so I uninstaled unbuntu from within windows

but then I burned the ubuntu iso on an cd and instaled it alongside windows

hardware was not working (well working now)
only issue now is graphics are very bad, and I want to look forward to playing games on ubuntu :(

I instaled unbuntu 10.4 on another hp laptop using wubi and it's working perfectly (after instaling drivers)


right so do you think uninstaling ubuntu is the best option?

---

### Post by amjjawad on 2010-09-12
> **beew said:**
> He wanted to try whether he could install the Nvidia driver, where would he install it if he couldn't write on the medium? 

Anyway I found the live CD a horrible way to try Ubuntu because it is so painfully slow, not to mention that you have to store the CDs and creating a live usb from iso is a lot faster than burning a CD, so if one has some usb sticks lying about and can boot from usb there is absolutely no reason to use a live CD those people keep giving out that advice as default. :)

Easy, he could download the driver on Ubuntu and that's all. The issue (from what I understood) isn't where to install? but it's how to get it work :)
I suggested to him a while ago to remove the current driver (because Ubuntu is telling him that driver is already in use) and install it again.


If someone has USB stick(s) and knows how to change the BIOS priority list, etc. CD/DVD is the default option but a big YES for USB :P 
Don't remind me :D I had to wait ages until I got something when I was booting from a CD.

---

### Post by beew on 2010-09-12
Installing Wubi is not a real installation, it is just a folder in Windows. If you want to experience the real thing, either do dual booting or install Ubuntu on an external usb drive or hard drive.   

Graphic drivers are somehow special, they are not like any other drivers because they are a part of the Linux kernel (as I understand) so you can't do anything unless you have a real installation. Your computer would start and would work for most thing without a wireless card but the Ubuntu desktop wouldn't even start without a graphic card.

---

### Post by dreadshroud on 2010-09-12
> **amjjawad said:**
> Easy, he could download the driver on Ubuntu and that's all. The issue (from what I understood) isn't where to install? but it's how to get it work :)
I suggested to him a while ago to remove the current driver (because Ubuntu is telling him that driver is already in use) and install it again.


If someone has USB stick(s) and knows how to change the BIOS priority list, etc. CD/DVD is the default option but a big YES for USB :P 
Don't remind me :D I had to wait ages until I got something when I was booting from a CD.

yea I've instaled the driver for it but it doesn't seem to work

the error I'm getting says run it from root? any idea how to try that?

---

### Post by amjjawad on 2010-09-12
> **dreadshroud said:**
> it didn't work when I instaled with wubi
so I uninstaled unbuntu from within windows

but then I burned the ubuntu iso on an cd and instaled it alongside windows

hardware was not working (well working now)
only issue now is graphics are very bad, and I want to look forward to playing games on ubuntu :(

I instaled unbuntu 10.4 on another hp laptop using wubi and it's working perfectly (after instaling drivers)


right so do you think uninstaling ubuntu is the best option?

Playing games on Ubuntu? didn't know there are games for Ubuntu :P

Yes, I'd suggest to uninstall it, get the 3 partitions back (I could show you how), use Microsoft Disc Manager to create a new partition so that you would have two partitions: 
C:
and
D:
Then Install Ubuntu on D: partition (Ubuntu will read it as /sdb) and choose: Use the Entire Disc - Option. That's your best chances.

In the mean time, I just want to know what you get when you reboot your laptop? can you tell me the options you get? I mean the boot menu?
Just want to make sure of something!

---

### Post by beew on 2010-09-12
> Easy, he could download the driver on Ubuntu and that's all. The issue  (from what I understood) isn't where to install? but it's how to get it  work

Which Ubuntu? I think there is only one copy, which is the one in the CD since that was before he actually installed it. Wubi is not Ubuntu and downloading it there wouldn't work, it wouldn't even work on a live usb with persistence.

---

### Post by amjjawad on 2010-09-12
> **beew said:**
> Installing Wubi is not a real installation, it is just a folder in Windows. If you want to experience the real thing, either do dual booting or install Ubuntu on an external usb drive or hard drive.   

Graphic drivers are somehow special, they are not like any other drivers because they are a part of the Linux kernel (as I understand) so you can't do anything unless you have a real installation. Your computer would start and would work for most thing without a wireless card but the Ubuntu desktop wouldn't even start without a graphic card.

My friend, he's telling you that he didn't use Wubi for his 2nd time of installation ;)

 					Originally Posted by **dreadshroud** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9838619#post9838619") 				
 				it didn't work when I instaled with wubi
so I uninstaled unbuntu from within windows

but then I burned the ubuntu iso on an cd and instaled it alongside windows

---

### Post by beew on 2010-09-12
If he has a real installation why are we talking about live CDs? I was making the point based on his earlier post that he wanted to try.

---

### Post by beew on 2010-09-12
Did he remove the noveau drivers? Or try the ppa I posted earlier, it worked for me.

---

### Post by amjjawad on 2010-09-12
> **beew said:**
> If he has a real installation why are we talking about live CDs? I was making the point based on his earlier post that he wanted to try.

We eliminated that option (live CD) in page 1 or 2 from this thread and now, we're page 4 ;)

Never mind, just forget it. I know how hard to keep track with everything :)

---

### Post by amjjawad on 2010-09-12
> **beew said:**
> Did he remove the noveau drivers? Or try the ppa I posted earlier, it worked for me.

He said he'll try that.

---

### Post by dreadshroud on 2010-09-12
> **beew said:**
> Installing Wubi is not a real installation, it is just a folder in Windows. If you want to experience the real thing, either do dual booting or install Ubuntu on an external usb drive or hard drive.   

Graphic drivers are somehow special, they are not like any other drivers because they are a part of the Linux kernel (as I understand) so you can't do anything unless you have a real installation. Your computer would start and would work for most thing without a wireless card but the Ubuntu desktop wouldn't even start without a graphic card.


I instaled it along side windows using the cd


the screen was blank, I did this inorder to "fix" it

1-put instalation disk in pc 
2-startup pc
3- press spacebar as soon as pic of keyboard/man shows
4-selected english as language
5-select try ubuntu without anychanges
6-press F6
7-select nomodesets
8-press esc
9- type           " i915. modset=0 xforcevesa
10-press enter

then I instaled it after trying, grub loader shows then blank screen

I used this "fix" to get around the problem

- press e while selecting first option in loader
-replace "queit splash" with nomodeset
- Ctrl+X to boot

after downloading and instaling the graphic card driver, it logs on without need of the second fix but I still can't change my reslution or acess nvidia settings (error as seen in first picture posted)

---

### Post by dreadshroud on 2010-09-12
> **amjjawad said:**
> Playing games on Ubuntu? didn't know there are games for Ubuntu :P

Yes, I'd suggest to uninstall it, get the 3 partitions back (I could show you how), use Microsoft Disc Manager to create a new partition so that you would have two partitions: 
C:
and
D:
Then Install Ubuntu on D: partition (Ubuntu will read it as /sdb) and choose: Use the Entire Disc - Option. That's your best chances.

In the mean time, I just want to know what you get when you reboot your laptop? can you tell me the options you get? I mean the boot menu?
Just want to make sure of something!

I get windows 7 loader/windows vista loader(which is strange becuase my laptop came with windows 7 preinstaled/ubuntu safemode/ubuntu

with wnumbers alongside them(I am assuming they are the version number), I can't post a screen shot of this sorry

---

### Post by uRock on 2010-09-12
> **dreadshroud said:**
> I get windows 7 loader/windows vista loader(which is strange becuase my laptop came with windows 7 preinstaled/ubuntu safemode/ubuntu

with wnumbers alongside them(I am assuming they are the version number), I can't post a screen shot of this sorry
W7 is Vista with upgrades, which is why the grub picks out the restore partition as being Vista.

---

### Post by amjjawad on 2010-09-12
> **dreadshroud said:**
> I get windows 7 loader/windows vista loader(which is strange becuase my laptop came with windows 7 preinstaled/ubuntu safemode/ubuntu

with wnumbers alongside them(I am assuming they are the version number), I can't post a screen shot of this sorry

No worries, I know you can't post a screen shot for that :)

Tha's great. I was trying to make sure of something.

Now, as I said, it's your call whether to try more with the driver or uninstall it then re-install it but not before you create new partition for Ubuntu using Windows 7 (I could show you how).

There's a bit of a problem here. It's getting too late and I have to sleep because I've spent 3 long days with my PC (sigh, it's a long story) and I really need to sleep now :)
Use your Windows at the moment and I could get back to you tomorrow. Is that fine? or perhaps you want someone else to show you how? I just installed Ubuntu today after long battle with my Hard Drives (I have 3) and ... hahaha, it's a long story. Point is, it's still fresh in my mind :P

---

### Post by dreadshroud on 2010-09-12
> **amjjawad said:**
> No worries, I know you can't post a screen shot for that :)

Tha's great. I was trying to make sure of something.

Now, as I said, it's your call whether to try more with the driver or uninstall it then re-install it but not before you create new partition for Ubuntu using Windows 7 (I could show you how).

There's a bit of a problem here. It's getting too late and I have to sleep because I've spent 3 long days with my PC (sigh, it's a long story) and I really need to sleep now :)
Use your Windows at the moment and I could get back to you tomorrow. Is that fine? or perhaps you want someone else to show you how? I just installed Ubuntu today after long battle with my Hard Drives (I have 3) and ... hahaha, it's a long story. Point is, it's still fresh in my mind :P

sorry for taking your time, thank you for your help 
I'll try reinstaling again and If it doesn't work out I'll try the partition thing
many thanks again

---

### Post by amjjawad on 2010-09-12
> **dreadshroud said:**
> sorry for taking your time, thank you for your help 
I'll try reinstaling again and If it doesn't work out I'll try the partition thing
many thanks again

You most welcome :) don't worry, I enjoy being here and that's why I installed Ubuntu. Beside, the best way and the fastest way to learn more about Ubuntu is to read about others' problems ;)

Don't waste your time and re-install Ubuntu on your current configuration. I don't think it would change anything. The partitioning is really important and by time you'll understand that very well :)

Oh, before I forget, try to BACKUP your system if you do have an external Hard Drive. It's very very very important in your case since you have only one HD with one partition for Windows :)

Take care and good luck!

---

### Post by dreadshroud on 2010-09-12
I removed the driver, restarted, installed the driver again
restarted but it gave me an error, and it can not configure  and gave me 4 options

-restart X
-use previous config
- run in low graphics just for this session
-reconfig

tried all options before and this time I selected run in low graphics just for this session

Still getting same error with Nvidia X Server Settings
how can I run it as root like it's telling me to? (first screenshot, [http://img534.imageshack.us/i/screenshotdre.png/](http://img534.imageshack.us/i/screenshotdre.png/))

---

### Post by beew on 2010-09-12
[http://ubuntuforums.org/showthread.php?t=1470206](http://ubuntuforums.org/showthread.php?t=1470206)

Here is one thread where the problem was solved.

---

### Post by amjjawad on 2010-09-13
Hi again, I'm back :P

Is there any update regarding the issue?

---

### Post by amjjawad on 2010-09-13
[http://i55.tinypic.com/51kew.jpg](http://i55.tinypic.com/51kew.jpg)

This screen shot will help you to understand how your HDD will look like after partitioning :)
I'm using my friend's laptop now and I did this one for you to show you an example.

---

### Post by dreadshroud on 2010-09-13
> **beew said:**
> [http://ubuntuforums.org/showthread.php?t=1470206](http://ubuntuforums.org/showthread.php?t=1470206)

Here is one thread where the problem was solved.

thank you very much, the issue is the same 
I'll try it out now and see if it works

---

### Post by dreadshroud on 2010-09-13
[http://ubuntuforums.org/showpost.php?p=8748678&postcount=16](http://ubuntuforums.org/showpost.php?p=8748678&postcount=16)

I'm not sure how to do that exactly
I downloaded the file in windows, but what to do from there?
do I put the downloaded file in a hard drive then boot to Ubuntu?


 'Place EDID raw file in /etc/X11"
where is /etc/X11?

---

### Post by dreadshroud on 2010-09-13
help anyone?

---

### Post by gerald3092 on 2010-09-13
As you installed from Wubi..... with the dual boot (windows + linux) give it 180 seconds to load. This may vary slightly.... the black screen with blinking white dash at top left is what it is supposed to be doing.... I have found on Netbook using Wubi that Ubuntu takes about just over 2 minutes to load which is half the time of Windows if you have security software and other start up programs to fully load. 

Again, the black screen with blinking white dash means Ubuntu is indeed loading.... they don't run the Windows type splash screens etc. Now on another netbook, this one, I wiped windows (erased) and installed Ubuntu Netbook Edition and it completely boots and starts up within seconds (and I do mean seconds), and that opposed to minutes on windows. Amazing ! 

PS.... consider Windows Registry clean up with installing, unistalling, reinstalling. This can be necessary with Wubi, as it will not reinstall with left over Windows Explorer folders (after uninstall) and/or Windows Registry keys. Search both looking for "Wubi" and "Ubuntu". Need help - [http://bluecollarpc.us/windowsregistry.php](http://bluecollarpc.us/windowsregistry.php) (webmaster).

---

### Post by dreadshroud on 2010-09-14
> **gerald3092 said:**
> As you installed from Wubi..... with the dual boot (windows + linux) give it 180 seconds to load. This may vary slightly.... the black screen with blinking white dash at top left is what it is supposed to be doing.... I have found on Netbook using Wubi that Ubuntu takes about just over 2 minutes to load which is half the time of Windows if you have security software and other start up programs to fully load. 

Again, the black screen with blinking white dash means Ubuntu is indeed loading.... they don't run the Windows type splash screens etc. Now on another netbook, this one, I wiped windows (erased) and installed Ubuntu Netbook Edition and it completely boots and starts up within seconds (and I do mean seconds), and that opposed to minutes on windows. Amazing ! 

PS.... consider Windows Registry clean up with installing, unistalling, reinstalling. This can be necessary with Wubi, as it will not reinstall with left over Windows Explorer folders (after uninstall) and/or Windows Registry keys. Search both looking for "Wubi" and "Ubuntu". Need help - [http://bluecollarpc.us/windowsregistry.php](http://bluecollarpc.us/windowsregistry.php) (webmaster).

I didn't instal from wubi, and I got most of my laptop working now
It's just my graphic card driver which is the problem

Could you please tell me how to follow the instructions in the posted fix?

---

### Post by beew on 2010-09-14
> I removed the driver, restarted, installed the driver again
restarted but it gave me an error, and it can not configure  and gave me 4 options

-restart X
-use previous config
- run in low graphics just for this session
-reconfigOK, instead of restarting, you should do as the screen shot said first, "run as root" means running a command with "sudo". So after installing the drivers, open a terminal and type
```

sudo nvidia-xconfig
``` then restart and it should work. Sorry, missed that post yesterday or I would have told you earlier. :)

---

### Post by dreadshroud on 2010-09-15
> **beew said:**
> OK, instead of restarting, you should do as the screen shot said first, "run as root" means running a command with "sudo". So after installing the drivers, open a terminal and type
```

sudo nvidia-xconfig
``` then restart and it should work. Sorry, missed that post yesterday or I would have told you earlier. :)

still doesn't work :(

---

### Post by beew on 2010-09-17
Hmm.. Still doesn't work? That is strange.

Hope this link would help.

[http://trycatch.iblogger.org/tips-n-tricks/how-to-install-nvidia-drivers-in-ubuntu-10-04-lucid-lynx]("http://trycatch.iblogger.org/tips-n-tricks/how-to-install-nvidia-drivers-in-ubuntu-10-04-lucid-lynx")

---

### Post by mastablasta on 2010-09-17
> **dreadshroud said:**
> [http://ubuntuforums.org/showpost.php?p=8748678&postcount=16](http://ubuntuforums.org/showpost.php?p=8748678&postcount=16)
 
I'm not sure how to do that exactly
I downloaded the file in windows, but what to do from there?
do I put the downloaded file in a hard drive then boot to Ubuntu?
 
 
'Place EDID raw file in /etc/X11"
where is /etc/X11?
 
/etc/X11 is a folder/directory in Linux
 
there is a way to see linux from windows. i think total commander used to have a plugin for this.
but easier way would be to boot to Linux and then just move the file from windows partition to the mentioned folder.
----
 
also i see on one of your previous posts how you "solved your problem " with enable vesa. i am not sure but i think this enables the nowadays "low graphics mode". and is usually ment to get you through the start so you can later install propper drivers from the drivers menu.
 
also don't count on being able to play the latest Windows games on Linux.

---

### Post by dreadshroud on 2010-09-19
my screen is still ugly

I've fixed all other issues, sound/wireless switch

but not this graphics issue :(
do you think the graphics problem is due to the hard drive partition that amjawad reffered to?

---

### Post by candtalan on 2010-09-19
> **dreadshroud said:**
> my screen is still ugly

I've fixed all other issues, sound/wireless switch

but not this graphics issue :(
do you think the graphics problem is due to the hard drive partition that amjawad reffered to?

Have you done this yet?
Place EDID raw file in /etc/X11

---

### Post by dreadshroud on 2010-09-21
> **candtalan said:**
> Have you done this yet?
Place EDID raw file in /etc/X11

ahh theres my problem

I thought it copied and pasted normaly, but appearently permisions is preventing me from doing so

it says the folder belongs to "root" and I can't change permisions

---

### Post by beew on 2010-09-21
> **dreadshroud said:**
> ahh theres my problem

I thought it copied and pasted normaly, but appearently permisions is preventing me from doing so

it says the folder belongs to "root" and I can't change permisions

You can become root temporarily by doing alt+F2 then type ```
gksudo nautilus
``` or make the file accessible by changing its ownership, in the terminal ```
cd directory-where-file-is-stored 
sudo chown your-usr-name filename
```

---

