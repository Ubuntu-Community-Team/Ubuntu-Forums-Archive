---
title: "boot memtest problem"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by gokul2411s on 2009-12-25
Dear sir/madam,

I am in one heck of a problem. Please help. Following is the description of the problem.

Initially I had Windows 7 on my C partition. I had a D partition with some data on it. I wanted to install Ubuntu and so I shrunk my C partition by 80Gb. I defined 3 partitions there , one for Linux root, one for /home and the other for Linux swap space. I installed Linux as per the instructions and I am nearly certain I did it right. I know this because I got a popup saying Linux was installed and that it is time to reboot. Well like a sincere end-user I rebooted. And the devil struck me.

When the computer booted, **MEMTEST** started up. Initially, I thought it was part of the installation process. Later I learnt that it was a RAM check tool. Fair enough! But now I am not able to boot into Windows or Linux at all. Even after patiently waiting for the entire check to get completed, I do not get an option to enter my operating system. Neither do I get that option before entering memtest. 

Please help with this problem.

Yours sincerely
[COLOR=#888888]Gokul Subramanian.[/COLOR]

---

### Post by audiomick on 2009-12-25
Hallo.
It sounds like your boot loader is confused. If you are using 9.10, this will be grub2, and older Ubuntu will have grub legacy.

I can't give detailed instructions, I haven't had enough to do with it, but there is documentation here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

for grub legacy here:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

The first thing to do is to check the default boot option. Memtest is a boot option, and I think it is conceivable that the has become the automatic boot preference instead of one of your Systems.

The next step would be to re-install grub as described in the documentation.

---

### Post by audiomick on 2009-12-25
double post

---

### Post by MooPi on 2009-12-25
Maybe something a bit more simple. Just after Bios prompt, you will need to press shift key. This should enter you into Grub. If everything is there boot to recovery. In recovery type ```
sudo update-grub
```Reboot and hopefully grub will be set properly.

---

### Post by drs305 on 2009-12-25
gokul2411s,

Welcome to Ubuntu and the Ubuntu forums. Sorry your first exposure to Ubuntu is causing some problems.

As audiomick suggested, check out the Grub 2 link and go to the Command Line section. Follow the steps there if you are able to get to the Grub 2 menu. For some reason Grub 2 is either defaulting to MEMTEST or it can't find your OS. 

If you don't see the Grub 2 menu during boot, hold down the SHIFT key during boot and it should show the G2 menu. From there, select your OS if depicted or go to the command line mode to try to boot into the OS.

If you see all the OSs but it defaults to MEMTEST, you can change the default boot item by following the steps in the "G2-Tasks" link in my signature line.

Additionally, from a terminal if you are able to get into Ubuntu, if you don't see your Windows install run "sudo update-grub". You can open a terminal from the Ubuntu desktop via Applications, Accessories, Terminal.

If you have further problems or questions search this forum or just post them here. You will find this forum very helpful.

---

### Post by gokul2411s on 2009-12-25
First of, I would like to thank you guys for the really fast response. But bad news. When I hit shift key, the list comes up but with only memtest86+.

I think I will have to reinstall right? Since I had installed from a frugal copy on my hard disk, and I cannot access that right now, I would like to know if there is a shortcut way of reinstalling Linux if thats what is the right thing to do.

Gokul.

---

### Post by drs305 on 2009-12-25
> **gokul2411s said:**
> First of, I would like to thank you guys for the really fast response. But bad news. When I hit shift key, the list comes up but with only memtest86+.

I think I will have to reinstall right? Since I had installed from a frugal copy on my hard disk, and I cannot access that right now, I would like to know if there is a shortcut way of reinstalling Linux if thats what is the right thing to do.

Gokul.

I don't understand the "frugal copy" reference. I'm writing this from the point of view of using a normal Ubuntu LiveCD for installation. If that isn't the case then some or all of this post may not be applicable.

When you see the memtest menu, you could try to manually boot to the Ubuntu OS using the commands listed in the "Command Line Interface" section of the Grub 2 community doc. It would only take 5 minutes or less to see if it works.  On the other hand, somewhere the installation wasn't completed normally and you may find it quicker to reinstall than trying to find out exactly what parts of the installation failed.

There really isn't a shortcut way that will probably help you other than trying to reinstall Grub 2 (instructions in the community doc) - that may work and would take about 10 minutes including the time to boot to the Ubuntu desktop from a livecd.

---

### Post by gokul2411s on 2009-12-25
Okay will try a reinstall. But let me have a few things clear about Linux installation. Should I have to specify a partition for each of the folders such as /, /home, /boot etc. I did so for / and /home but I didnt do anything like that for /boot. Would that be a possible cause of the problem?

---

### Post by joes7 on 2009-12-25
I had the same prob, re-instatalling GRUB should fix it.

---

### Post by drs305 on 2009-12-25
> **gokul2411s said:**
> Okay will try a reinstall. But let me have a few things clear about Linux installation. Should I have to specify a partition for each of the folders such as /, /home, /boot etc. I did so for / and /home but I didnt do anything like that for /boot. Would that be a possible cause of the problem?

Not normally. Most people don't use a separate /boot partition and don't have problems. Advanced users with lots of different OSs sometimes want to keep a separate partition devoted especially for /boot, but unless you already know you want one, you probably don't need it. ;-)

---

### Post by Troll_the_Great on 2009-12-25
> **gokul2411s said:**
> Okay will try a reinstall. But let me have a few things clear about Linux installation. Should I have to specify a partition for each of the folders such as /, /home, /boot etc. I did so for / and /home but I didnt do anything like that for /boot. Would that be a possible cause of the problem?

No, you don't have to specify a partition for /boot, just for / and for /home (but this only if you want to have a separate home partition - which is a good idea by the way).
But wouldn't be easier to try repairing GRUB first, and then, if it doesn't work, to reinstall?
Cheers!

---

### Post by gokul2411s on 2009-12-25
Ok I downloaded the live installation CD once again and put the .iso file on my external hard disk, which the website claims can be used as a boot device. 

But when I put my USB drive in and boot, I get the following errors: 

PXE-E61: edia test failure, check cable
PXE-MoF: Exiting Broadcom PXE ROM
Operating system not found

On my boot preferences, the order is

Cd
USB
HD
etc..

Any ideas on this one..

---

### Post by gokul2411s on 2009-12-25
erratum in previous post: edia is 'media'

---

### Post by drs305 on 2009-12-25
Did you try just reinstalling G2 as joes7 suggested? 

Anyway, in response to your current questions. The .iso can be placed on a hard drive and run, but as far as I know it has to be mounted and then run.  As far as I know, you can't just put the iso in a folder and have it boot. I don't know which website you were referring to so I can't visit it to see what is posted there.

Can you burn it to a CD and install Ubuntu from the resulting disc? That eliminates a lot of the problems - finding USB drives, splitting the install between two drives, etc.

---

### Post by gokul2411s on 2009-12-25
Well Joes has suggested I reinstall but I am not sure how to do that.. Coz I am accustomed to the simple GUI operation of Windows, I am not very clear in my mind what is going on. I am ashamed I cant even reinstall in Linux.

---

### Post by gokul2411s on 2009-12-25
Btw, if it helps you troubleshoot, when I type in 'ls' at the grub command, it lists the following

hd0   hd0,7  hd0,6   hd0,5   hd0,3   hd0,2  hd0,1.


Clearly hd0,4 is missing. Here is some background info. According to me, hd0,1 is some dell utilities.. hd0,2 and hd0,3 are C and D drives on my Windows. The remaining 3 are root, home and swap. Or so all are supposed to be.

I checked out a few websites which suggest manual boot methods by typing in some commands as follows.

set root(hd0,5)
linux /vmlinuz/root=/dev/sda5 ro
etc..


But as soon as I type the linux command, it says file not found

Does all this serve any purpose??

---

### Post by drs305 on 2009-12-25
There is no shame in not knowing how to do something in Linux. Maybe only shame in not being willing to learn, which is clearly not your situation.

There doesn't have to be a hd0,4. Primary partitions start at 0, but the first extended partition in linux always starts at 5. So hd0,4 may not exist. That is ok. Your ubuntu partitions are most likely 5: system, 6 /home, 7 swap.

To reinstall Grub 2, you would start the Ubuntu LiveCD, go to the Desktop, and open a terminal from the Main Menu: Applications, Accessories, Terminal.

Then follow the instructions here:
[https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

There are really only a few steps required and if you go slowly you should be able to reinstall Grub 2.

As for the "file not found" message: In the same document is a section on booting from the grub or grub-rescue prompt. Try going to the "grub-rescue" section if you didn't already and be sure to run the "set prefix..." line. Note: When you enter it you won't get any feedback, but it is storing the information you entered.

From the grub prompt, you should also be able to run the following command after setting the prefix and root locations to view the contents of your /boot system folder. In your case, hdX,Y should most likely be hd0,5

```

ls (hdX,Y)/boot

```
Example: ls (hd0,5)/boot

---

