---
title: "Ubuntu keeps crashing every 5 minutes!!!!!"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by rcbfour on 2011-08-06
Just installed 11.04 on a pc that was running a 2002 version of xp. An '04 or '05 emachines desktop with 2 gb of ram, 160 gb hd, amd 64 athlon with ati radeon xpress 200 graphics and a USB 2.0 airlink101 wifi adapter (and an aol sticker), with the 32 bit version of 11.04. My problem is that it keeps crashing. I deleted xp but I still have the xp install disk. When I'm doing even web surfing in chromium, the tabs keep crashing, and it eventually konks out with a white screen that has stripes, and it's different colors and patterns every time. Are there any fixes, or should I just go back to using xp?&#57433;&#58387;&#58384;&#57379;&#58371;

---

### Post by rcbfour on 2011-08-06
Update: my problems occur when I'm using the web browsers (chromium and firefox)

---

### Post by scruffyeagle on 2011-08-06
> **rcbfour said:**
> Just installed 11.04 on a pc that was running a 2002 version of xp. An '04 or '05 emachines desktop with 2 gb of ram, 160 gb hd, amd 64 athlon with ati radeon xpress 200 graphics and a USB 2.0 airlink101 wifi adapter (and an aol sticker), with the 32 bit version of 11.04. My problem is that it keeps crashing. I deleted xp but I still have the xp install disk. When I'm doing even web surfing in chromium, the tabs keep crashing, and it eventually konks out with a white screen that has stripes, and it's different colors and patterns every time. Are there any fixes, or should I just go back to using xp?&#57433;&#58387;&#58384;&#57379;&#58371;

My 2 cents: Unless some guru pops up w/ good advice, I'd say yes go back to using XP. But, don't completely abandon Ubuntu. I'd:
1) Repartition the HD to be
1a) Partition 1: Primary bootable 40 GB for XP to live in,
1b) Partition 2: Primary 18 GB for Ubuntu v10.04 64-bit to live in,
1c) Partition 3: Extended 2 GB for Ubuntu's swap space,
1d) Partition 4: Extended 20 GB Ext4 for Linux-only backup copies of programs & files,
1e) Partition 5: Extended 80 GB NTFS for storage XP can access. (Ubuntu can use this area too. You'd just want to limit what you put there to stuff usable in both OS's.)

2) Re-install XP into Partition #1.

3) Obtain a copy of Ubuntu v10.04 LTS 64-bit version, and install it into Partition #2.
3a) During installation, Grub will be installed into the MBR. It will automatically set up a dual-boot mechanism.

4) Work w/ your new installation of 64-bit Ubuntu to see if your display problem still exists in the new setup.

I advise the v10.04 LTS, because it's the primary stable distro. (If you've got a major problem, go back to basics and the most stable distro you can get your hands on.) I advise the 64-bit, because that's what your CPU functions on. The 64-bit version is labelled "amd64"... Using 32-bit only uses half of your CPU's capability, and might even be a cause of problems via mismatch.

---

### Post by scottstensland on 2011-08-06
Have you gone the route of seeing whether your graphics driver is the cause ?
I had similar symptoms (with stock ubuntu on my nvidia machine) and solution
was to purge the default ubuntu graphics driver and install nvidia drivers.

---

### Post by Rex Bouwense on 2011-08-06
Did you try 11.04 before you installed it?  If you did, was everything working?  I don't believe that using a 32 bit OS on a 64 bit capable machine has anything to do with your problems.  Have you tried to use classic instead of unity?

---

### Post by nickleboyblue on 2011-08-06
Your problem doesn't come from using 32 bit OS on a 64 bit machine.  Like others have already stated, get an Ubuntu install cd with 10.04 (NOT 11.04, as there is much less support for it at the moment, and you might consider going to an even earlier version of ubuntu), and try it out before installing it.  If it works, (don't worry about the speed, it will be slow from the optical drive), install it.  If not, you should probably go back to XP, and if I were you, I wouldn't even bother with manually re-partitioning.  simply format the hard drive so it will be compatible with XP and install it again.

If Ubuntu still gives you problems, you don't want to go back to XP, AND you're in an adventurous mood, go ahead and try something like Suse, Fedora, Cent OS, Puppy, or some other distro.  I've gotten hours of entertaining tinkering with messing around with other distros.  Also, avoid the most recent versions.  They might claim to have the most support, but they are also designed for the newest hardware.  So, steer clear of Unity and Gnome 3, and possibly even KDE 4, though KDE is probably more likely to work than the other two in newer versions.

Hope this helps!

---

### Post by rcbfour on 2011-08-06
Thank you! this is my first time using the forums, and im really pleased to have quick, useful responses. im downloading the 10.04.3 iso as i speak, and i really hope it works. if not than i may try another distro or something else. thanks for helping me, because i really want this to work. oh, and i installed the 32 bit version because the 64 bit one didn't work. thanks again, and i hope to contribute more in the future

---

### Post by amjjawad on 2011-08-07
Hello and Welcome,

First thing first, do NOT even think to go back to XP, otherwise I have to come myself and install Ubuntu on your machine ... just kidding :D

But seriously, you haven't tried yet lots of other suggestions so hold your horses and let's go with this one by one ... ready? good :)

1- After you download whatever version of Ubuntu that works for you, **whether** 11.04 (which has ALL the support you might think of but that doesn't mean a magical solutions for problems) **OR** 10.04.3, please ... make sure to check MD5SUM.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2- Decide whether you want to create a LiveCD or LiveUSB?
Here is how to make each: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
Just check point #2.

3- Boot your machine from the LiveCD or LiveUSB. Remember, if you want to go  for LiveUSB, you MUST change your BIOS settings and tell your machine to boot first from USB instead of your Hard Drive.

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]


4- Make sure that everything works fine and Ubuntu detects your Hardware and work fine with that.

5- If everything is OK then you are good to go.

6- If you DO NOT have any important files/data on your machine, you can wipe your HDD and start installing from scratch. If you DO have some important files, PLEASE make sure to back these files up before anything else :)

7- My own approach is to create the partitions and prepare the HDD before installation. Some might disagree with me or have another opinion but this is what I would do. 

If you decide to go with 11.04 then Point your Mouse to the Shutdown Icon on the top bar and choose "System Settings" then "GParted".

If you decide to go with 10.04.3 then:

System > Administration > GParted.

8- If you are planning to Dual-Boot Windows and Ubuntu, then:
[http://ubuntuforums.org/showpost.php?p=11101707&postcount=129](http://ubuntuforums.org/showpost.php?p=11101707&postcount=129)

If you are planning to install Ubuntu only, then just ignore the NTFS part (which is step 3 in that link I just posted).

9- Click on Install Ubuntu from your Desktop and follow the steps.

10- Please, have a look at this: [http://ubuntuforums.org/showpost.php?p=11101891&postcount=131](http://ubuntuforums.org/showpost.php?p=11101891&postcount=131)

This is very important specially if you're Dual-Booting.
If you are installing Ubuntu as the only system on your machine, then ignore it but again, you'll need it in the future when you'll Dual-Boot ;)

In my signature, there is a guide for Dual-Booting, have a look in case you're planning to Dual-Boot with Windows.

11- After installation, login to Ubuntu and please report back if you have any issue or question.

12- Done.

Good luck :)

---

