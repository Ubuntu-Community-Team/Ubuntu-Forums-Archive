---
title: "Here comes a headache...Ubuntu problems"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by wmb on 2011-01-10
I had Windows 7 installed, I then installed Ubuntu1(the 1 is for the sake of clarity) inside of W7. I updated Ubuntu1 and could no longer boot, so I just did a clean install of Ubuntu2 (separate from W7) so I could work on a project. I then uninstalled Ubuntu1 from W7, so I had W7 and Ubuntu2 side by side.

At the end of the semester, I decided to do a clean W7 reinstall. I can no longer access Ubuntu2 because Bill Gates likes to lower the productivity of anyone that gets in the way of Microsoft (I kid...).

I go through some tutorials of trying to get grub back online, but I miserably fail. I probably screwed up the flux capacitor or something. Anywho...

I installed Ubuntu3 alongside Ubuntu2 and W7 hoping it would fix the grub crap. Apparently it did not.  My PC boots straight into Ubuntu3. It's a 250GB HD and there are 204GB free.

Every time I type ```
su
``` and my password, I am met with ```
su: Authentication Failure
```I don't know why it's saying that...I used the same password as I did on my other Ubuntu install...

I'm at my wits' end right now, and it's probably due to the fact that I'm not having any luck with these tutorials. :confused: 

Help?

edit:
Goo! I got into root...just not the way I thought I would...

following [this]("http://ubuntuforums.org/showthread.php?t=224351") tutorial...
```
root@matt-Studio-1555:~# grub
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
root@matt-Studio-1555:~# find /boot/grub/stage1
find: `/boot/grub/stage1': No such file or directory
root@matt-Studio-1555:~# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000085ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29165   234259456   83  Linux
/dev/sda2           29165       30402     9936897    5  Extended
/dev/sda5           29165       30402     9936896   82  Linux swap / Solaris


```W7 is gone isn't it? LOL

Anywho, luckily I didn't lose anything important...people may want to be careful because I know I didn't have it to where Ubuntu3 was going to install on 200+ GB, it was supposed to be around 30something...

---

### Post by mastablasta on 2011-01-10
Well Wubi is not really ment to be upgrading or updating as it still has issues.... it's ment for trying. people usually don't read the FAQ's and manuals. but don't worry there is some solution have a look here:
 
[http://ubuntuforums.org/showpost.php?p=10324197&postcount=2](http://ubuntuforums.org/showpost.php?p=10324197&postcount=2)
 
edit: the above is just solution to Wubi problem.
 
 
tutorial you followed is for old system.
 
You can run bootinfoscript to let you see if windows is still there. here is the script: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) post results here. 
 
and here is more information about the grub new ubuntu is using: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
 
i think you could have solved your issue (before at least) if you only type in:
 
sudo update-grub 
that way GRUB would be updated and you would see both ubuntu and windows.
 
 
you only saw windows before because windows overwrite GRUB with it's own boot loader MBR. and all you need to do then is to basically replace it with grub.

---

### Post by bcbc on 2011-01-10
> **wmb said:**
> I had Windows 7 installed, I then installed Ubuntu1(the 1 is for the sake of clarity) inside of W7. I updated Ubuntu1 and could no longer boot, so I just did a clean install of Ubuntu2 (separate from W7) so I could work on a project. I then uninstalled Ubuntu1 from W7, so I had W7 and Ubuntu2 side by side.

At the end of the semester, I decided to do a clean W7 reinstall. I can no longer access Ubuntu2 because Bill Gates likes to lower the productivity of anyone that gets in the way of Microsoft (I kid...).

I go through some tutorials of trying to get grub back online, but I miserably fail. I probably screwed up the flux capacitor or something. Anywho...

I installed Ubuntu3 alongside Ubuntu2 and W7 hoping it would fix the grub crap. Apparently it did not.  My PC boots straight into Ubuntu3. It's a 250GB HD and there are 204GB free.

Every time I type ```
su
``` and my password, I am met with ```
su: Authentication Failure
```I don't know why it's saying that...I used the same password as I did on my other Ubuntu install...

I'm at my wits' end right now, and it's probably due to the fact that I'm not having any luck with these tutorials. :confused: 

Help?

edit:
Goo! I got into root...just not the way I thought I would...

following [this]("http://ubuntuforums.org/showthread.php?t=224351") tutorial...
```
root@matt-Studio-1555:~# grub
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
root@matt-Studio-1555:~# find /boot/grub/stage1
find: `/boot/grub/stage1': No such file or directory
root@matt-Studio-1555:~# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000085ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29165   234259456   83  Linux
/dev/sda2           29165       30402     9936897    5  Extended
/dev/sda5           29165       30402     9936896   82  Linux swap / Solaris


```W7 is gone isn't it? LOL

Anywho, luckily I didn't lose anything important...people may want to be careful because I know I didn't have it to where Ubuntu3 was going to install on 200+ GB, it was supposed to be around 30something...
You probably installed 10.10? Apparently there have been problems with it's new installer overwriting windows due to some confusing interface.

For the future it's better to ask for help here - when you reinstall windows it replaces the grub bootloader, but this is a trivial fix to get Ubuntu back booting. Reinstalling is a last ditch thing to try - sometimes necessary, but usually not. It looks like you're following grub-legacy tutorials, not grub2 which Ubuntu has used since release 9.10 (so, for the future, any mention of menu.lst or /boot/grub/stage1 is grub-legacy)

@mastablasta - windows is gone, so wubi is gone too.

---

### Post by TechWiz2100 on 2011-01-10
su gives you issues because in Ubuntu the correct syntax is sudo su with your password.

---

### Post by jerremy-tamlin on 2011-12-07
> **TechWiz2100 said:**
> su gives you issues because in Ubuntu the correct syntax is sudo su with your password.

You can also do ```
sudo -i
``` which seems to do the same thing. See "man sudo" for details.

---

### Post by lisati on 2011-12-07
> **jerremy-tamlin said:**
> You can also do ```
sudo -i
``` which seems to do the same thing. See "man sudo" for details.

Also see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

