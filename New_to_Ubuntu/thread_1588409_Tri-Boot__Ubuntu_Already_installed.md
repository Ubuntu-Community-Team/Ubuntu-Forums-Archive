---
title: "Tri-Boot | Ubuntu Already installed"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by sjhaffner on 2010-10-04
I have a 250 gb HD with Ubuntu 10.10 already installed. I also have an 80 GB HD which I want to split into two 40 GB partitions. On the two partitions I want to install Windows XP and Windows 98. 

My question:  :confused:

How do I install the other two os's and get asked on boot which OS to boot into?

I hope I'm not being too confusing, and any help is extremely useful.
Thanks in advance.

---

### Post by sandyd on 2010-10-04
> **sjhaffner said:**
> I have a 250 gb HD with Ubuntu 10.10 already installed. I also have an 80 GB HD which I want to split into two 40 GB partitions. On the two partitions I want to install Windows XP and Windows 98. 

My question:  :confused:

How do I install the other two os's and get asked on boot which OS to boot into?

I hope I'm not being too confusing, and any help is extremely useful.
Thanks in advance.

take out the 250 from the computer
install xp and 98 (not sure why you want 98, but w/e)
stick the 250 back in and run
```

sudo fdisk -l
```
and post the output

also, have you considered running xp and 98 in virtual machines?

---

### Post by oldfred on 2010-10-05
Not sure about win98 but this works for the newer versions. You need to move boot flag to second partition before install. Does 98 need FAT, I do not remember anymore.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by Dustin2128 on 2010-10-05
> **sandyd said:**
> 
also, have you considered running xp and 98 in virtual machines?
Or giving xp the partition and running 98 in a vm. I can't imagine you're going to need 3D accel on 98...
whichever way you do it, just make sure windows doesn't install its own bootloader, then you can just boot to ubuntu and ```
sudo update-grub
```

---

### Post by amjjawad on 2010-10-05
I didn't want to start new thread because this scenario is similar to mine.

I have Ubuntu installed on an external HDD (what I'm using now to write this) and I had a problem with my internal HDD (XP installed) so had to wipe everything.

I know it's highly recommended to install Windows FIRST then Ubuntu but as I said, I had a problem and I don't want to re-install Ubuntu again.

I'm not sure how to do that boot flag thing but this is what I'm going to do. Please, correct me if this is wrong:

1- I'll reboot my PC.
2- Turn my External HDD off.
3- Install Windows XP (actually it's not an installation, I'll restore the backup image that I have).
4- Reboot my PC
5- Turn on my External HDD (where Ubuntu is installed)
6- Set the HDD priority so that my PC will boot first from the external HDD (this is my current settings now but when I turn the external HDD off, the boot sequence will be changed so have to set it back as it's now - External HDD 1st then internal HDD 2nd).
7- Save and exit.
8- Rebooting
9- Hopefully I'll get the GRUB and boot into Ubuntu
10- Run 
```
sudo update-grub
```


Please, correct me if this is wrong.
Otherwise, I don't think there's another way to do that.

Note that: Ubuntu's boot loader is installed on the external HDD (obviously).

Thank you :)

---

### Post by amjjawad on 2010-10-05
> **sjhaffner said:**
> I have a 250 gb HD with Ubuntu 10.10 already installed. I also have an 80 GB HD which I want to split into two 40 GB partitions. On the two partitions I want to install Windows XP and Windows 98. 

My question:  :confused:

How do I install the other two os's and get asked on boot which OS to boot into?

I hope I'm not being too confusing, and any help is extremely useful.
Thanks in advance.

I'd suggest to install Windows XP and NOT to install Windows 98. It's been 10 years or more since I've used it (Win98 ) but if I'm not mistaken, you might not be able to dual boot to all these OS's or there's more chance of failure at some point.

---

### Post by halj32 on 2010-10-05
first disconnect your Linux HDD
the other disk make to partitions one fat 32 maybe 10gig for Win 98
the other make it NTFS or fat32 doesnt matter for XP
first install win 98, then winXP
when finished reconnect your Linux HDD
boot in to Ubuntu and do a grub update
next boot you should get boot ubuntu or XP, if XP then it'll be 98 or xp

---

### Post by amjjawad on 2010-10-05
> **amjjawad said:**
> I didn't want to start new thread because this scenario is similar to mine.

I have Ubuntu installed on an external HDD (what I'm using now to write this) and I had a problem with my internal HDD (XP installed) so had to wipe everything.

I know it's highly recommended to install Windows FIRST then Ubuntu but as I said, I had a problem and I don't want to re-install Ubuntu again.

I'm not sure how to do that boot flag thing but this is what I'm going to do. Please, correct me if this is wrong:

1- I'll reboot my PC.
2- Turn my External HDD off.
3- Install Windows XP (actually it's not an installation, I'll restore the backup image that I have).
4- Reboot my PC
5- Turn on my External HDD (where Ubuntu is installed)
6- Set the HDD priority so that my PC will boot first from the external HDD (this is my current settings now but when I turn the external HDD off, the boot sequence will be changed so have to set it back as it's now - External HDD 1st then internal HDD 2nd).
7- Save and exit.
8- Rebooting
9- Hopefully I'll get the GRUB and boot into Ubuntu
10- Run 
```
sudo update-grub
```


Please, correct me if this is wrong.
Otherwise, I don't think there's another way to do that.

Note that: Ubuntu's boot loader is installed on the external HDD (obviously).

Thank you :)

Anyone?

---

### Post by oldfred on 2010-10-05
amjjawad,

It depends on your backup image. If it was a drive image & you restore will it not restore the entire drive. Does the image include the PBR or partition boot sector? You may have to repair that. If not restored to exactly the same partition number you will have to edit or rebuild the boot.ini as it has drive & partition in it. Not sure what else may be an issue. Windows does not like hardware changes and usually wants to call home to verify.

---

### Post by spydeyrch on 2010-10-05
> **halj32 said:**
> first disconnect your Linux HDD
the other disk make to partitions one fat 32 maybe 10gig for Win 98
the other make it NTFS or fat32 doesnt matter for XP
first install win 98, then winXP
when finished reconnect your Linux HDD
boot in to Ubuntu and do a grub update
next boot you should get boot ubuntu or XP, if XP then it'll be 98 or xp


halj32 said it perfectly!!

I currently have a triple boot system with three different hdd. But the concept is the same. 

I typically go a little over board when do setups to try and determine/prevent any issues in the future. So this is what I would do in your case, sjhaffner:

Key:

-HDD1  ->  Ubuntu HDD (250 GB, right?)
-HHD2  ->  98/XP HDD (80 GB, right?)

Steps:

*NOTE* - I would recommend reading through these steps first and understanding each one and the desired results, before doing them. - /*NOTE*

1.) with power off, disconnect hdd2 from machine. a disconnect can simply be the power cable connected to the hdd. no need to completely & physically remove it from the machine. we just don't want it spinning up when the machine starts.

*NOTE* - You may need to change some of your BIOS settings to boot from hdd1 in step #2. - /*NOTE*

2.) turn on machine and see if you can boot into ubuntu. if so, great!!!  :biggrin::biggrin: This was just to check if GRUB is in fact installed onto your ubuntu machine. (Yes I know that one could run some quick commands in a terminal to check this but I didn't want to bother with it. If someone else would like to share how to do this, please feel free to do so.) Ya never know if there are going to be any issues due to improper grub installations (previous multi-boot system, different upgrades, etc.) better safe and check than sorry later.

3.) turn off machine. disconnect hdd1.

4.) re-connect hdd2

*NOTE* - You may need to change some of your BIOS settings to boot from hdd2 in step #5. - /*NOTE*

5.) partition hdd2 into two partitions. what ever size you want. just make sure you meet the minimum requirement for each 98 & XP for their respective partitions. also, you can use ubuntu to pre-partition hdd2 or you can use the 98 cd during the install. perhaps the easiest would be to just use the 98 cd during install at this point.

6.) install 98 to first partition of hdd2. after installation, turn off machine.

7.) insert xp install cd and boot from it. install xp to second partition. XP should automatically detect 98 and add it to XP's boot menu.

8.) After installation of XP, reboot (with XP install CD removed from the machine). check to see that both 98 and XP show up in XP's boot menu. 

9.) If you can see both, select 98 to check and see if you can actually boot into it. If yes, reboot.

10.) at XP boot menu, select XP this time to check if able to properly boot. If yes shutdown machine.

*NOTE* - you may need to change some settings in your BIOS to boot from hdd1 in step #11. /*NOTE*

11.) re-connect hdd1. make sure tha both hdd1 & hdd2 are connect to the machine. boot from hdd 1 and into ubuntu.

12.) once booted and logged into ubuntu, open a terminal and type the following command:

```
 sudo update-grub2 
```this should run and update your grub boot menu. It should detect your windows installations and add them to grub. At the very least it will add xp to grub.

13.) once finished updating grub via that command, restart your machine.

14.) confirm at the grub boot menu that you can view and select the other two operating systems (98 & XP). Again, at the very least you should see XP (and obviously ubuntu plus grub's normal selections (memtest, recovery mode, etc etc)).

15.) select one of your windows installs from the grub menu and boot into it to check and make sure everything works.

*NOTE* - if only xp is the only one visible (out of the two windows OSes) in the grub menu, select it. It should then show you the windows boot menu and give you the option of xp or 98. /*NOTE*

VIOLA! you should now have a triple boot system up and running. Don't forget to update your 98 & XP installs with all their security updates, drivers, etc. Although, as it has been mentioned before, I would recommend just installing only XP on hdd2 (the 80 GB hdd) and running 98 from within a VM. You could run the VM either from within XP or Ubuntu or have it accessible from both, so that way no matter which OS you are running, you could start up your win98 VM!!!  8)8)\\:D/\\:D/

Hopefully that helps and clarifies things.

Again, halj32 stated it perfectly, I decided to just expound a little more on what was stated previously.

-Spydey

P.S. Depending on how old/new your machine's hardware is, 98 may not even be able to run on it at all. No drivers for it due to newer parts and the os being >10+ years old.  Hence the best option would really be to run it in a VM. If you would like some help setting up a VM, I would be more than happy to help you with getting it setup and working properly. I have about 5 different VMs on each of my 3 primary OS that I have. I am no expert with VMs but I should be able to help get you up and running. And if there is a problem, the Ubuntu community is a great resource for help. :-D

---

### Post by spydeyrch on 2010-10-05
> **amjjawad said:**
> I didn't want to start new thread because this scenario is similar to mine.

I have Ubuntu installed on an external HDD (what I'm using now to write this) and I had a problem with my internal HDD (XP installed) so had to wipe everything.

I know it's highly recommended to install Windows FIRST then Ubuntu but as I said, I had a problem and I don't want to re-install Ubuntu again.

I'm not sure how to do that boot flag thing but this is what I'm going to do. Please, correct me if this is wrong:

1- I'll reboot my PC.
2- Turn my External HDD off.
3- Install Windows XP (actually it's not an installation, I'll restore the backup image that I have).
4- Reboot my PC
5- Turn on my External HDD (where Ubuntu is installed)
6- Set the HDD priority so that my PC will boot first from the external HDD (this is my current settings now but when I turn the external HDD off, the boot sequence will be changed so have to set it back as it's now - External HDD 1st then internal HDD 2nd).
7- Save and exit.
8- Rebooting
9- Hopefully I'll get the GRUB and boot into Ubuntu
10- Run 
```
sudo update-grub
```
Please, correct me if this is wrong.
Otherwise, I don't think there's another way to do that.

Note that: Ubuntu's boot loader is installed on the external HDD (obviously).

Thank you :)

From what I have read, you should be fine. I don't know if there is any difference but from what I have read, the correct code to update grub is:

```
 sudo update-grub2 
```

ubuntu 10.04 uses the new grub2 and not the legacy grub. but the old legacy grub commands might work. never tried the old ones with grub2 so cant really say for sure.

-Spydey

---

### Post by amjjawad on 2010-10-05
> **oldfred said:**
> amjjawad,

It depends on your backup image. If it was a drive image & you restore will it not restore the entire drive. Does the image include the PBR or partition boot sector? You may have to repair that. If not restored to exactly the same partition number you will have to edit or rebuild the boot.ini as it has drive & partition in it. Not sure what else may be an issue. Windows does not like hardware changes and usually wants to call home to verify.

Hi oldfred,

I'm not quite sure what exactly you mean but my backup image has the entire partition where Windows XP was installed. I was using that backup image, I mean I restored XP from it and it was working without any problem for 10 days.

Now, looks like GParted didn't shrink my sdb (where Windows XP was installed) correctly so I lost the whole thing and had to wipe the whole drive.

If I'm not mistaken, my backup image has the boot loader and I guess you mean the MBR not PBR :P

I guess I'll turn my external HDD off, install Windows XP, Fedora, make sure both are loading correctly and smoothly then I'm going to turn my external HDD ON and change the boot sequence in BIOS. Of course, update-grub is required. I'll do exactly like what I suggested previously. I was in need to someone to confirm my plan is right :)

Thanks!

---

### Post by amjjawad on 2010-10-05
> **spydeyrch said:**
> From what I have read, you should be fine. I don't know if there is any difference but from what I have read, the correct code to update grub is:

```
 sudo update-grub2 
```

ubuntu 10.04 uses the new grub2 and not the legacy grub. but the old legacy grub commands might work. never tried the old ones with grub2 so cant really say for sure.

-Spydey

Looks like I'll be fine because so far, no one disagreed with me. I'll wait more hopefully I get more advice/opinion about that.

It doesn't matter :)
Both update-grub and update-grub2 work fine. I just did that "update-grub" and it works.
Ubuntu uses grub2, that's right but again both commands are correct.

---

### Post by amjjawad on 2010-10-05
I'm reading now a very nice guide ([https://help.ubuntu.com/community/MultiOSBoot](https://help.ubuntu.com/community/MultiOSBoot)). I really hope I could find some answers over there.

So far, I came to know that my scenario is the opposite of what had been written on that guide. 
When I installed Ubuntu, I didn't choose to install the boot loader in the MBR because Windows was installed first. Now, Windows has gone.

I'm still waiting to read more thoughts/suggestions from you guys :)

---

### Post by oldfred on 2010-10-05
amjjawad since this is not your thread and now it has morphed into more than the OPs original question please start a new thread.

Please post this so we can see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by amjjawad on 2010-10-05
> **oldfred said:**
> amjjawad since this is not your thread and now it has morphed into more than the OPs original question please start a new thread.

Please post this so we can see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

This thread is very similar to my scenario. Instead of Windows 98, I'm trying to install Fedora 13.

Do you think it's still better to start a new thread?

I'm sorry if I started something on here while it's my thread but again, I found it very close to my problem. That's all.

---

### Post by oldfred on 2010-10-05
Boot issues almost always are unique as everyone's configuration is different. Where did Fedora come from, we were discussing dual boot with windows.

---

### Post by amjjawad on 2010-10-05
> **oldfred said:**
> Boot issues almost always are unique as everyone's configuration is different. Where did Fedora come from, we were discussing dual boot with windows.

Forget Fedora. Let's stick with Windows and Ubuntu.

I wrote about "Fedora" because it's "Tri-Boot" thread. Anyway, sorry again.

---

