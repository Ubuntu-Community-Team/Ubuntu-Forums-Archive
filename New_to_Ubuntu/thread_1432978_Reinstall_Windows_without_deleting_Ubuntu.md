---
title: "Reinstall Windows without deleting Ubuntu"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by philipp42 on 2010-03-18
Hi guys
 
I recently tried to find the solution to my problem in other threads but I could not find the exact answer to my problem.
I am posting in the beginner talk because my experiencelevel with ubuntu is quiet low.
 
So here the problem:
My windwos is dead and I have to install a new version but I don't want to damage my ubuntu. Right now I am using both operation systems.
My Harddisk has to partions, one of them I use for both systems: for ubuntu as well as windows, what do you think about that? Should I prefer to use for each system a different partion?
My disk has a sapce of 500 gb, when I installed Windows I estableshed two parts, one of 400 gb for all my data and another of 100 gb for windows and ubuntu. After installing Windows I installed Linux splitting the secound partion of 100 gb, 40 gb for Windows and 60 gb for ubuntu, but this secound split only is recongised by ubuntu not by windows.
Now as I told you my windos doesn't work anymore and I want to reinstall it, I had windows xp home editon and now I want to change to XP professional, which steps are necesary without damaging my ubuntu?
I got a Windows CD and I think I will be able to get a ubuntu-live cd.
 
If there are any information missing, please let me know and if some sentences can't be understood I would be glad to explain them better.
 
Thank you for helping me out!
 
Greetings
Philipp

---

### Post by Pougnet on 2010-03-18
So you have a primary partition for your data, an extended partition with two logical drives for ubuntu and windows?

---

### Post by natravis on 2010-03-18
Open a terminal (Apps -> Accessories -> Terminal) and copy and paste the following into it
```
sudo fdisk -l
```

This will give us a list of the partitions and help us guide you through the install. Please copy the output to a reply and wrap it with the [ code] and [ /code] tags (omit the space between "[" and the "c" or "/").

---

### Post by rahulshah on 2010-03-18
First of all never install both operating systems on the same partition. It could cause security related issues. 
Secondly, insert your windows professional cd and install it in the same partition in which you currently have windows. Nothing will happen to your linux files only you wont be able to boot into it.
After that insert the linux cd and choose an option called 'rescue os'. that will install the grub and all will be fine....

I hope that helps....

---

### Post by J V on 2010-03-18
Backup your data first: if theres anything you learn from windows, its that it will wipe out everything even when you tell it not to, just for kicks...

---

### Post by penguinv on 2010-03-18
I'll tell you what I have done, sucessfully.
This was on a Dell. I'm saying that in case it makes a difference.

I have "reinstalled" windows.  I have installed a sp2 over an sp1 and NOT HARMED MY WUBI installation. 

I think I've even put the same sp2 over the sp2 when I thought something was munged.

I forgot what the choice was. It was not the "reinstall or repair" choice I have been told about and was anticipating - "Pick Repair because Reinstall will reformat your hard drive, son."

I did not lose 
- any programs
- any data

But I did lose entries in my All Programs for programs that were -still there -still installed -but had no entries in the All Programs menu (If I'd only had a desktop icon) so I had to go find the exec file and make an alias.

This was obviously XP and it was Home.

Best of luck.

---

### Post by Elcid247 on 2010-03-18
> **philipp42 said:**
> Hi guys
 
I recently tried to find the solution to my problem in other threads but I could not find the exact answer to my problem.
I am posting in the beginner talk because my experiencelevel with ubuntu is quiet low.
 
So here the problem:
My windwos is dead and I have to install a new version but I don't want to damage my ubuntu. Right now I am using both operation systems.
My Harddisk has to partions, one of them I use for both systems: for ubuntu as well as windows, what do you think about that? Should I prefer to use for each system a different partion?
My disk has a sapce of 500 gb, when I installed Windows I estableshed two parts, one of 400 gb for all my data and another of 100 gb for windows and ubuntu. After installing Windows I installed Linux splitting the secound partion of 100 gb, 40 gb for Windows and 60 gb for ubuntu, but this secound split only is recongised by ubuntu not by windows.
Now as I told you my windos doesn't work anymore and I want to reinstall it, I had windows xp home editon and now I want to change to XP professional, which steps are necesary without damaging my ubuntu?
I got a Windows CD and I think I will be able to get a ubuntu-live cd.
 
If there are any information missing, please let me know and if some sentences can't be understood I would be glad to explain them better.
 
Thank you for helping me out!
 
Greetings
Philipp

from what ur saying i get u have this layout

40  GB Windows
60  GB Ubuntu
400 GB Data

right?

did u install ubuntu using live CD (stand alone installation)? or wubi (install inside windows)?

if it was a **wubi** installation, i'm sorry but ur ubuntu is gone (unless there is [some sort of a hack]("http://ubuntuforums.org/showthread.php?t=438591") for it)

if it was a **stand alone installation**, then u can simply reinstall windows on ur 40 GB partition without any worries of damaging ur ubuntu installation, since its on a separate drive so u won't format it but, it will disappear from the boot menu because windows will overwrite the MBR (master boot record) which is the place where the boot menu is placed and u will only be able to boot into windows, but u can restore it using a ubuntu live CD.

Here is how:

after u reinstall windows, boot the live CD and then mount ur ubuntu drive (the 60 GB) and run this command in a terminal

```
sudo grub-install --root-directory=/media/UR_60_GB_DRIVE_MOUNT_NAME /dev/sda
```

this will reinstall grub into ur MBR.

hope i've helped :)

NOTE: i know this can be intimitating at first but its simple and all of this info is straight of google. [Recovering Grub After Windows Reinstall]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") is where i got the command from, it is a really badly written how-to though.

---

