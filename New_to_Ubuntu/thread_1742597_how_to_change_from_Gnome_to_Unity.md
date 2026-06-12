---
title: "how to change from Gnome to Unity"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by vivin_west on 2011-04-29
I just upgraded Linux from 10.10 to 11.4. Want to know how to change the desktop from Gnome to Unity

---

### Post by VMC on 2011-04-29
> **vivin_west said:**
> I just upgraded Linux from 10.10 to 11.4. Want to know how to change the desktop from Gnome to Unity

We need to know more about your system. For one you need to install the 3d drivers for your video. Once that is installed on reboot, it should default to Unity, providing you have the Ubuntu selected on the login boot screen, and not Ubuntu Classic.

---

### Post by mikewhatever on 2011-04-29
Select 'Ubuntu'  at the login screen.

---

### Post by vivin_west on 2011-04-29
The only three options I get in my sessions screen right now is Gnome, Xterm and Failsafe Gnome. I want to know what 3D drivers I need to install. Compiz for eg works fine.

---

### Post by mikewhatever on 2011-04-29
Interesting. Can you post the outputs of the following commands:
```
cat /etc/lsb-release

dpkg -l | grep unity
```

If compiz works as expected, you must already be using the 3d driver for your card.

---

### Post by sikander3786 on 2011-04-29
> **vivin_west said:**
> The only three options I get in my sessions screen right now is Gnome, Xterm and Failsafe Gnome. I want to know what 3D drivers I need to install. Compiz for eg works fine.
Are you sure the upgrade was successful? Please post the output of this command from your Terminal.

```
lsb_release -a
```

---

### Post by vivin_west on 2011-04-29
Oh you are right. Still stuck on 10.04

Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid

This is strange. can you advice what is the terminal command for upgrade?

---

### Post by sikander3786 on 2011-04-29
> **vivin_west said:**
> Oh you are right. Still stuck on 10.04

Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid

This is strange. can you advice what is the terminal command for upgrade?
First install all the updates for you current release.

```
sudo apt-get update && sudo apt-get upgrade
```

Then you'll need to upgrade from 10.04 > 10.10 and then to 11.04 step-by-step. It is also advised in some cases to remove your graphics driver before upgrading.

```
update-manager -d
```

---

### Post by Sef on 2011-04-29
1) > It is also advised in some cases to remove your graphics driver before upgrading

Remove any proprietary drivers before upgrading.

2) **Back up** your **data** first. No 100% guarantees that all will go well.

3) Have a 10.04 disk available in case the upgrade fails.

---

### Post by mikewhatever on 2011-04-29
Hope you are aware that you'll be upgrading to Ubuntu 10.10, and not to the just released 11.04.

---

### Post by vivin_west on 2011-04-29
Yup. I realize that it will be 10.10 and then 11.04. 
But I did not understand what are proprietary drivers. I haven't installed any hardware drivers. Even the drivers for the graphics card i guess were installed when installing 10.04.

---

### Post by sikander3786 on 2011-04-29
> **vivin_west said:**
> Yup. I realize that it will be 10.10 and then 11.04. 
But I did not understand what are proprietary drivers. I haven't installed any hardware drivers. Even the drivers for the graphics card i guess were installed when installing 10.04.
Look under System > Administration > Hardware Drivers. Any activated there?

And it will also be helpful to post the output of this command.

```
lspci | grep VGA
```

---

### Post by mikewhatever on 2011-04-29
There are closed source drivers for Nvidia/ATI cards. If you don't have one of those, then you don't need to bother about proprietary drivers.

---

### Post by vivin_west on 2011-04-29
Ok now I am in a fix!! I dint disable the video drivers. The system is not loading. It says Gnome power driver not installed correctly. What to do next?  any suggestions?

---

### Post by beew on 2011-04-29
Why don't you just do afresh install?? I have no idea why people recommend upgrading when you have two versions to upgrade and have proprietary graphic card. Even if everything goes smoothly (not likely unless you have a very pristine installation with little customization) it will take > 2 hours while a fresh install takes about 20 minutes. Things are more likely to go wrong if it takes that long (say you lose your internet during upgrade)

---

### Post by rocka on 2011-04-29
I'm in a fix too, like the OP in this thread.
I have just upgraded from 10.10 t0 11.04, and now I don't have any video at all - it just boots straight to a fullscreen terminal and a command line. Please see my thread at [http://ubuntuforums.org/showthread.php?t=1742752](http://ubuntuforums.org/showthread.php?t=1742752)

Like the OP in this thread, I wasn't aware that I had any proprietary drivers. I have done several updates to this system over the last few years, all the previous upgrades have gone smoothly.

---

### Post by beew on 2011-04-29
> **rocka said:**
> I'm in a fix too, like the OP in this thread.
I have just upgraded from 10.10 t0 11.04, and now I don't have any video at all - it just boots straight to a fullscreen terminal and a command line. Please see my thread at [http://ubuntuforums.org/showthread.php?t=1742752](http://ubuntuforums.org/showthread.php?t=1742752)

Like the OP in this thread, I wasn't aware that I had any proprietary drivers. I have done several updates to this system over the last few years, all the previous upgrades have gone smoothly.

Instead of wasting time to trouble shoot a blotched upgrade just do a fresh install, will take only 20 minutes. :)

---

### Post by madjr on 2011-04-29
> **beew said:**
> Instead of wasting time to trouble shoot a blotched upgrade just do a fresh install, will take only 20 minutes. :)

i second this. 25 minutes here in new partition, no headaches.

and if it doesnt work for you for what ever reason, you can always go back to your old install and yet avoid another headache. :)

---

### Post by rocka on 2011-04-29
I'm not sure how I would "just do a fresh install" at this stage: the machine as it sits now is effectively not working [well, not getting past the command line stage, anyway].

Are you telling me that the required install files would all be sitting there on that hard drive now? How would I find them, and then, how would I install from there?

I've got to admit, I would be nervous about overwriting stuff - there's not much empty space on it...
If it comes to it, I may be able to buy another hard drive [I was going to sooner or later anyway] but still the issue is how to actually get the files needed for the fresh install. Maybe I could download it using this netbook, then put it on a thumb drive, then figure out how to boot the desktop from the usb...

eeewww...
:(

---

### Post by beew on 2011-04-29
> **rocka said:**
> I'm not sure how I would "just do a fresh install" at this stage: the machine as it sits now is effectively not working [well, not getting past the command line stage, anyway].

Are you telling me that the required install files would all be sitting there on that hard drive now? How would I find them, and then, how would I install from there?

I've got to admit, I would be nervous about overwriting stuff - there's not much empty space on it...
If it comes to it, I may be able to buy another hard drive [I was going to sooner or later anyway] but still the issue is how to actually get the files needed for the fresh install. Maybe I could download it using this netbook, then put it on a thumb drive, then figure out how to boot the desktop from the usb...

eeewww...
:(

Boot into a live usb or live CD for 11.04, then install with it. It will wipe all the mess off your hard disk in the process, so I hope you have backed up important stuffs before the blotched upgrade.

---

### Post by vivin_west on 2011-04-29
I noticed I dint take back up of one small drive that has some important files. I need to fix this issue. Can anyone help me?

---

### Post by rocka on 2011-04-29
> **beew said:**
> Boot into a live usb or live CD for 11.04, then install with it. It will wipe all the mess off your hard disk in the process, so I hope you have backed up important stuffs before the blotched upgrade.

<shudder>
I think I might have to go buy a new HDD in the morning, install onto that one, then stick the old one in an external USB case and retrieve the files from there...

---

### Post by beew on 2011-04-29
> **vivin_west said:**
> I noticed I dint take back up of one small drive that has some important files. I need to fix this issue. Can anyone help me?

In that case when you reinstall with the live usb/cd, choose manual partition.You need to make 3 partitions: a / partition about 15 -20 g, a /home partition to store your data and settings, it should be as big as you need. Both of these should be formatted as ext4. Then a third, swap partition (Linux swap) whose size should be about 1.5x ram.

NOW DO NOT TOUCH THE SMALL PARTITION WHICH YOU HAVEN'T BACKED UP.  Depending on your lay out, try to make the /home partition adjacent to it if possible.

After install, access the small partition from Ubuntu and retrieve those files. Then boot into the live usb/cd again and use gparted to expand /home to the small partition now that you don't need it any more.

Other possibilities:

1)You may be able to remove your hard drive, hook it to another Ubuntu machine and use that to access the small partition to retrieve those files, then you put the drive back into the computer and do a fresh install wiping everything out. 

2) If you can fit your data into 2 G, make a Ubuntu live usb wit persistence,--you will also use it for install,-- boot into it and use it to retrieve those data, and then do the fresh install and wipe the hard drive.

---

### Post by vivin_west on 2011-04-29
I am using WUBI. Can I do the same that you mentioned using a Ubuntu un a USB?

---

### Post by beew on 2011-04-29
> **vivin_west said:**
> I am using WUBI. Can I do the same that you mentioned using a Ubuntu un a USB?

I don't use WUBI and I don't recommend it as it adds many unnecessary complications and IMO it is not real Linux install since it needs Windows :) So I don't know how to fix your problem but no,WUBI doesn't work on usb because it lives in Windows.

Maybe this guy bcbc will help you, he's the WUBI guy around here. Post it on a WUBI thread you will get better chance to find help there. :)

---

