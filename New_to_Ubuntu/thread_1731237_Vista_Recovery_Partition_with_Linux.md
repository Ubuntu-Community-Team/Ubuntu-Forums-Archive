---
title: "Vista Recovery Partition with Linux"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by ZareCograth on 2011-04-16
Ok, sorry if this has been asked before, but couldn't find anything on google for this exact problem. I have a laptop with Windows Vista. I don't have any recovery CDs, but I have a recovery partition. I'm getting tired of my OS being slow and have been wanting to try out Linux for a while. My concern is if I switch to Linux and find out I don't like it, I need to make sure I can put Vista back on my computer. So, my question is as long as I keep the recovery partition for Vista on my laptop, can I still install Linux on the rest of my HD and be able to recover to Vista if I want to?

---

### Post by wilee-nilee on 2011-04-16
I would make a image a clone of the vista, hard to say if the recovery partition will be accessible.

---

### Post by hansdown on 2011-04-16
Welcome to the forum, ZareCograth.

You need to make recovery discs for your vista install, then you can always go back, if you choose.

---

### Post by 3177 on 2011-04-16
> **ZareCograth said:**
> Ok, sorry if this has been asked before, but couldn't find anything on google for this exact problem. I have a laptop with Windows Vista. I don't have any recovery CDs, but I have a recovery partition. I'm getting tired of my OS being slow and have been wanting to try out Linux for a while. My concern is if I switch to Linux and find out I don't like it, I need to make sure I can put Vista back on my computer. So, my question is as long as I keep the recovery partition for Vista on my laptop, can I still install Linux on the rest of my HD and be able to recover to Vista if I want to?

no, if you install an OS on your entire HDD, recovery partition or not, you cannot go back.
I would recomend using wubi to install INSIDE windows first, or a vbox.

---

### Post by K_45 on 2011-04-16
That may work, but I'd manually partition Ubuntu to make sure the recovery stays put. Even better dual-boot Ubuntu with Vista, and keep both Vista and its recovery partition:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by 3177 on 2011-04-16
> **K_45 said:**
> That may work, but I'd manually partition Ubuntu to make sure the recovery stays put. Even better dual-boot Ubuntu with Vista, and keep both Vista and its recovery partition:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

for a  beginners sake I'd say use wubi instead of a dual boot(you know how ubuntu 10.10 likes to likk windows bootloader). If its for someone who doesn't really know linux, wubi is the best bet as they can just delete ubuntu if worst comes to worst. otherwise they are screwed as they dont have a cd(personal experience, my wife).

---

### Post by Sef on 2011-04-16
Use the partitioner that comes with Vista and dual boot. I would try a Live CD or Live USB for a while to make sure it can do what you need it for.

---

### Post by K_45 on 2011-04-16
> **3177 said:**
> for a  beginners sake I'd say use wubi instead of a dual boot(you know how ubuntu 10.10 likes to likk windows bootloader). If its for someone who doesn't really know linux, wubi is the best bet as they can just delete ubuntu if worst comes to worst. otherwise they are screwed as they dont have a cd(personal experience, my wife).

Aaah yes, the wife acceptance factor aka WAF.

---

### Post by Blasphemist on 2011-04-16
Don't you love it that we all have strong opinions but don't all agree?

Please post what your machines details are and for instance storage space available might cause us to more fully agree. What you post for details will actually allow us to judge if you should be lumped in with the wife mentioned or considered a capable noob like many of us. 

As was posted you can use the live cd or usb to see what the basic Ubuntu is and ensure it runs on your machine, though there is some performance hit due to running from the cd or usb. Usually the only question about whether or not it will run as is, is what video controller you have.

---

### Post by ZareCograth on 2011-04-16
My HD has 80 GB total. 10 GB for the recovery partition, and the rest for everything else. Right now I have about 26 GB of free space. My Processor is an AMD Turion(tm) 64 X2 Mobile Technology TL-56 1.80 GHz. I have 1 GB RAM. As for video controller... I admit I'm at a loss on what that is. If its what I think then its an ATI Radeon Xpress Series.

---

### Post by 3177 on 2011-04-16
> **ZareCograth said:**
> As for video controller... I admit I'm at a loss on what that is. If its what I think then its an ATI Radeon Xpress Series.
```
lspci
```
post the output please

---

### Post by K_45 on 2011-04-16
I'd dual-boot with that, but I'd run the Ubuntu live cd to make sure there are no hardware problems. Also, I'd use the x86 Xubuntu live cd on that system. To find your video run

```
lspci | grep "VGA"
```

---

### Post by ZareCograth on 2011-04-16
I'm not sure where to put that to give the output. Can you explain please?

---

### Post by Blasphemist on 2011-04-16
> **ZareCograth said:**
> My HD has 80 GB total. 10 GB for the recovery partition, and the rest for everything else. Right now I have about 26 GB of free space. My Processor is an AMD Turion(tm) 64 X2 Mobile Technology TL-56 1.80 GHz. I have 1 GB RAM. As for video controller... I admit I'm at a loss on what that is. If its what I think then its an ATI Radeon Xpress Series.

What do you think everyone, better than the wife would do? Most likely though I see many women on here that know much more than I do. 

You have bare minimum space available and could quickly fill your drive. You could likely get away with a wubi install for a while but I expect you'll be quickly ready to pitch Vista. 

Exactly what do you do on the machine? More specifically, what do you do that isn't done in a browser? And while trying the live cd or usb, go to any mission critical web sites you visit. Do you use office and if so, for what? 

I still have Windows 7 installed but very rarely ever boot it. Usually just to do windows and Kaspersky updates and ensure it's still working. And windows 7 is much better that vista IMHO. Kaspersky is going to run out in a couple months and then its goodbye windows for me. I think you should consider it.

---

### Post by Blasphemist on 2011-04-16
K-45 is saying to run that command from a terminal in the live cd. It looks like a DOS prompt plain text window.

---

### Post by ZareCograth on 2011-04-16
I usually just check out a few websites and play a few video games. The main video game right now that I play is Minecraft.

---

### Post by K_45 on 2011-04-17
> **ZareCograth said:**
> I'm not sure where to put that to give the output. Can you explain please?

In Applications -> Accessories -> Terminal.

---

### Post by 3177 on 2011-04-17
> **Blasphemist said:**
> What do you think everyone, better than the wife would do?

you got a lotta nerve. When my wife switched to ubuntu, she knew nothing other than what I had told her; but when it came to her games, she couldn't do anything.
She had EXACTLY the same system as the OP, Vista with a recovery partition that she believed would re install vista should she not like linux.
Telling someone new that has less than 30 Gigs of free space to dual boot  is !@#$$.
Vista needs 1/3 of its HDD to run smoothly.

I'm done with this thread, and i hope you dont screw this person the same way I did my wife, as I know they dont have a cd to fix what you screw up.

---

### Post by Blasphemist on 2011-04-17
I don't see minecraft, and know absolutely nothing about it, but there are 515 free games available. Check your websites to make sure there isn't one using something badly non standard while your on the live cd. Check out the games available in the software center and the ones that come standard.

---

### Post by K_45 on 2011-04-17
> **3177 said:**
> you got a lotta nerve. When my wife switched to ubuntu, she knew nothing other than what I had told her; but when it came to her games, she couldn't do anything.
She had EXACTLY the same system as the OP, Vista with a recovery partition that she believed would re install vista should she not like linux.
Telling someone new that has less than 30 Gigs of free space to dual boot  is !@#$$.
Vista needs 1/3 of its HDD to run smoothly.

I'm done with this thread, and i hope you dont screw this person the same way I did my wife, as I know they dont have a cd to fix what you screw up.

A fresh install is less than 3GB and the OP has mentioned browsing and a few games which should fit nicely in around 20GB. Shrinking the partition in Vista is also a viable option.

---

### Post by ZareCograth on 2011-04-17
Ok, what's with this LiveCD? Unfortunately its past midnight here right now so not willing to try something until the morning, but was trying to see if there was an easy way to do this. From what I gather I'd have to make an Image Clone of Vista just to be sure I can restore it if I decide I don't like Linux.

---

### Post by K_45 on 2011-04-17
[http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)

Burn the .iso with ImgBurn in Vista, then you can boot up from it. You want the [COLOR=Black][xubuntu-10.10-desktop-i386.iso]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.10/release/xubuntu-10.10-desktop-i386.iso")[/COLOR]

---

### Post by ZareCograth on 2011-04-18
Sorry, got real busy yesterday. Got the LiveCD running today, and after entering ispci my VGA compatible controller is ATI Technologies Inc RS482 [Radeon Xpress 200M] My biggest problem is I can't get wireless connection on the LiveCD.

---

### Post by Mark Phelps on 2011-04-18
> **ZareCograth said:**
> Sorry, got real busy yesterday. Got the LiveCD running today, and after entering ispci my VGA compatible controller is ATI Technologies Inc RS482 [Radeon Xpress 200M]...

With that old an ATI chipset, the only video drivers that will work now are the default open-source drivers.  The good news is that they are installed automatically with setup; the bad news is that if they don't give you the performance you want, you're stuck.  There are no restricted drivers that will work with your chipset and recent versions of Ubuntu (newer than 8.10).

---

### Post by ZareCograth on 2011-04-18
Well, my biggest problem right now is finding a way to install Vista back on my computer if I decide I don't like Linux. The LiveCD works, but I only have wifi for my laptop so using the LiveCD I can't connect to the internet. Also in order to find out if it runs to my liking I'd have to install a game that I like and see how well it runs it on Linux which requires me to install Linux instead of Vista.

---

### Post by mike555 on 2011-04-18
Sounds like your in for trouble , vista needs extra empty room for defrag and such (about 20% ) any less and it will not work good for long .
 I would suggest getting a bigger hard drive , then partition it and clone vista on it leaving some extra room , then install Linux to a partition by itself ...... if that is beyond what you want to do you could try installing ubuntu to a usb drive and grub to it ... if your computer can boot from usb.

---

### Post by ZareCograth on 2011-04-18
Well, the biggest problem with that idea is I have no way of reinstalling Vista onto a new HD. Plus every time I try to open up my laptop to look at my RAM and HD I feel like I'm going to break the outer casing. So, not sure if I keep missing a screw or if it's just catching on itself.

---

### Post by mike555 on 2011-04-19
If you get a new bigger HD , there are dozens of free programs to clone your install of Windows on to the new one ... like;  [http://www.snapfiles.com/get/easustodo.html](http://www.snapfiles.com/get/easustodo.html)

---

### Post by mikey73000 on 2011-04-19
):P   The best way i have found and safest is to remove vista drive and put used or new drive for Linux 10-10 that way its impossible to screw it up.   [SIZE=2]**[COLOR=Magenta]Really[/COLOR]**[/SIZE]

---

### Post by ZareCograth on 2011-04-20
Ok, gf actually had the Vista discs so I installed Ubuntu. Had a few problems installing a couple things but youtube helped me on that. Now I'm experiencing something I find strange. There is only one user account which is mine, but for some reason when I go to change a priority or drag files into certain folders it acts like I don't have the privileges needed to do such things. So can someone please tell me how to fix this?

---

### Post by OscarTango on 2011-04-20
Your account in Ubuntu is a user account, meaning it doesn't have root (Administrative) priviledges. Check out [RootSudo]("https://help.ubuntu.com/community/RootSudo") for more info.

---

### Post by Mark Phelps on 2011-04-21
You have root access by default in Ubuntu, you just have to ask for it ... and you do that by preceding a command with "sudo".

Thus, to open the Nautilus file manager as ROOT, just open the terminal and enter "sudo nautilus".

---

### Post by ZareCograth on 2011-04-21
Well I only have one user on this computer and its me. I have made myself an Administrator, but I still can't move files to certain places and can't change privileges. I have also noticed a few things that I downloaded told me to go to System > Preferences, but under System I don't have that folder. I actually have no folders just a few programs and none are the ones I'm looking for.

---

### Post by K_45 on 2011-04-21
Don't change privileges or modify system files unless you know *exactly *what you are doing.

---

### Post by Blasphemist on 2011-04-21
> **Mark Phelps said:**
> You have root access by default in Ubuntu, you just have to ask for it ... and you do that by preceding a command with "sudo".

Thus, to open the Nautilus file manager as ROOT, just open the terminal and enter "sudo nautilus".

OP, the above is right. Do you understand what he is saying and also the post warning not to change things without being sure you know what the affects will be.

You can have root privileges but you get it via sudo, not by being an administrator. This is part of why Linux doesn't have the windows virus and other problems.

---

### Post by rosencrantz on 2011-04-21
Ubuntu doesn't work like Windows in that respect. (it's much more intelligent ;-))
No one except the 'root' user (which is deactivated in standard Ubuntu) has full permissions for everything on the computer.
Standard users are allowed to change everything in their home folder, but have limited read/execute access to the system folders. Other users' home folders are fully unreadable.
The sudo command gives temporary full permissions to programs you run through it,
as in sudo cp x /usr/bin/x (copy x to the system folder /usr/bin).
This makes Linux extremely secure against intruders and incautious users - admin permissions are restricted to exactly those processes needing it and additionally password protected. 
'Normal' and slightly dangerous activities like running a web browser have only very limited permissions.

---

### Post by ZareCograth on 2011-04-21
Ok, that helps with moving a file to certain folders. Can someone please tell me why I don't have preferences under my Systems tab? I was wanting to change themes but can't find out how with out the preferences.

---

### Post by rosencrantz on 2011-04-21
No System->Preferences->Appearance? (see attached snapshot)
If you're on KDE, it's somewhere in System Settings.

---

### Post by ZareCograth on 2011-04-22
No, don't have that. Don't have KDE yet, but using Xubuntu or the other(can't remember what it's name is right now) I don't have any tabs under System. I have Additional Drivers, Gigolo, Language Support, Login Screen, Printing, Startup Disk Creator, Synaptic Package Manager, Task Manager, Time and Date, Ubuntu Software Manager, Update Managers, and Users and Groups. At the top left of my screen I have the tabs Applications, and Places instead of file like in the picture.

---

### Post by rosencrantz on 2011-04-23
The two lightweight desktops are XFCE (Xubuntu) and LXDE (Lubuntu). Neither of them have a lot of eye candy, so there isn't a lot to configure.
What you describe sounds like XFCE to me (I test loaded the Live CD images) - does this screenshot look more familiar?

Try the Appearance and Window Manager entries to configure your desktop.

---

### Post by K_45 on 2011-04-23
> **rosencrantz said:**
> The two lightweight desktops are XFCE (Xubuntu) and LXDE (Lubuntu). Neither of them have a lot of eye candy, so there isn't a lot to configure.
What you describe sounds like XFCE to me (I test loaded the Live CD images) - does this screenshot look more familiar?

Try the Appearance and Window Manager entries to configure your desktop.

Xubuntu is the very opposite of lightweight. Its a porky GNOME distro with an XFCE skin. XFCE should use less than 200mb of RAM on boot, not 500mb.

---

### Post by rosencrantz on 2011-04-24
Nevertheless, it seems to be what he is using :-)

---

### Post by K_45 on 2011-04-24
> **rosencrantz said:**
> Nevertheless, it seems to be what he is using :-)

True.:)

---

### Post by ZareCograth on 2011-04-24
Sorry, was out of town for the weekend, but yes that is what I'm using. Thanks now I can change my settings. Can't think of any other problems with Linux itself. Right now its just trying to get my game to run a little faster, but don't think that has anything to do with Linux. If anyone has any suggestions on how to get my game to run a little faster I'd be more then happy to hear. Thanks for all your help.

---

