---
title: "Testing with GParted LiveCD"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by Bartender on 2009-08-25
Several recent posts regarding partitioning motivated a little research.  I've often encouraged folks to use a Gparted LiveCD instead of the partitioner that's built into the Ubuntu LiveCD.  Both partitioners use gparted, and they both look the same.  But the Gparted LiveCD (GPLCD) works more reliably than the Ubuntu LiveCD (UCD).  I believe one reason is that GPLCD does not mount any partitions, whereas the UCD mounts swap if it sees one.

Anyway, I went into this little exercise to get a better grip on two things.  

One, it's fairly easy to take screenshots for posting to the forums from a UCD.  How much harder is it to take screenshots from within GPLCD?

Two, how come the GPLCD seems to fail to run the monitor more often than the UCD, and what can you do about it?

I came up with six different PC/HDD/graphics card/monitor combinations.    

Test #1 – an ASUS P5GDC-V Deluxe ATX motherboard, running onboard 915 Intel graphics chipset, and Linux Mint on a PATA HDD.  Hooked to a 20” CRT.

 Test #2 – the ASUS P5GDC-V again, but this time with a SATA HDD and W2K.  Same CRT.

Test #3 – an ASUS CUSL2-C motherboard, running a 1GHz PIII and an ASUS/Nvidia V9400-X AGP graphics card.  Spinning a PATA HDD with Qimo (Qimo is an educational variant of Xubuntu).  Connected to same CRT monitor as above.

Test #4 – Acer 5920 laptop, unknown motherboard, Intel GM965 graphics, dual-boot Vista/Ubuntu 8.10 on the OEM HDD.

Test #5 – Same Acer 5920, spinning a Seagate Momentus 7200 RPM drive, Jaunty installed.

Test #6 – Dell Precision 470 workstation, running an Intel (I think) dual-CPU Xeon board, ASUS/Nvidia EN8400GS PCI-x graphics card, and a dual-boot XP/Jaunty PATA 120GB HDD.  23” Acer LCD monitor.

[SIZE="4"]**Saving Screenshots to Thumbdrive from GPLCD**[/SIZE]

First off, here are instructions for saving screenshots from GPLCD, provided by a kind soul on the Gparted Forums.

_____________________________________________________________

Copying a "GParted" Screenshot to an USB-Stick
1. Be sure, that your Boot medium is first in Boot sequence ( and NOT the USB Stick).
2. Plug-in the USB-Stick.
3. Boot "GParted Live"
4. When "GParted" stops scanning, look for the device name of your stick.
(I use as example "sdb1"; replace "sdb1" with your device's name, wherever it's used.)
5. Open "Terminal" window. Type at the prompt and confirm with [Enter] after each line.
"Mounting" the stick
```
mkdir /mnt/usb
```
```
mount /dev/sdb1 /mnt/usb
```
```
mkdir /mnt/usb/screenshot
```
6. Take a screenshot ( only one at a time, because file name is always "gparted.jpeg" )
7. Store screenshot to USB Stick
Copying to stick ( source to target)
```
cp  /root/gparted.jpeg   /mnt/usb/screenshot/gp_01.jpg
```
(Use a different number for the second and all other screenshots.)
You could also use "mc" (Midnight Commander) file manager for copying.

_______________________________________________________________

I used the same thumb drive, moving it from system to system.  The “mkdir /mnt/usb/screenshot” command creates the “screenshot” folder on the thumb drive, so it only needs to be entered the first time.  As long as you're using the same thumb drive and haven't erased the “screenshot” folder, the folder will be found when you enter the last of the four command lines, which sends the screenshot to the thumb drive.

In other words, once the screenshot folder has been created on the thumb drive, you only need the first, second, and fourth command lines to mount the thumbdrive and save the shot to that folder on the thumb drive.  There's a big camera icon on the GParted desktop, so taking the shot is easy.  It always saves to /root/gparted.jpeg, so that part's easy too.   Moving the screenshot to the thumbdrive is a little trickier, but I used the instructions successfully for all of these screenshots and I'm no Linux guru.

All of the test PC's were set to boot either from the optical drive first, or from USB ports before optical, so I waited until I heard the GPLCD start to spin up before plugging in the thumb drive.

I used a CD made from the GpartedLiveCD.iso 4.5-3 download.

[SIZE="4"]**Testing the PC's  **[/SIZE]

First up, the P5GDC-V Deluxe, which has historically been fussy about LiveCD's and Linux.  I think it has something to do with the way it recognizes HDD's.  The only method that did not give me a blank monitor was to choose the “Failsafe Mode” at the first Gparted screen.  After several screens rolled past, some indicating many errors, I chose the “Forcevideo” mode, then picked the default settings in Forcevideo option.  Easier than it sounds.

The results?  Please refer to “test_01.jpeg”.  / is installed to a primary partition, then there's  an extended partition for swap and /home.  This is one step up from an automatic Linux installation, where you would see only two partitions.  
Notice the odd terminology for the PATA HDD.  “hde” indicates that this is the fifth HDD in the system.  Again, I think it has something to do with the odd way this motherboard has always identified HDD's.  Maybe it's a setting in BIOS.  I would have no problem using GPLCD to partition this drive, but wanted to point out the funny numbering to illustrate that it helps to experiment a little bit, and don't panic.

Next up, the ASUS P5GDC-V again, this time with a SATA HDD.  Windows 2000 installed.  Illustrated in “test_02.jpeg”.  Nothing much to see here.  One big NTFS primary partition.  I don't know how 7.84 MB of space got left out.  “sda” is more like what we would expect to see.  I had to go thru the same steps as above to get GPLCD to display anything on the monitor.

Third test: the CUSL2-C, an older Pentium III -era ASUS desktop motherboard.  I picked the “Default” settings in Gparted's first window and the partitioner came up just fine.  No hassles getting a screen.  “test_03.jpeg” shows the results; a little 10GB HDD running a Xubuntu variant called Qimo.  The PATA HDD is recognized as “hda”.  Again we have a primary partition, and an extended “box”.  / is mounted to hda1, swap is mounted to hda5, and /home is mounted to hda6.  700+ MB of RAM inside, so I should have made the swap a little bigger if I wanted to use “suspend”.

Test #4:  an Acer 5920 laptop.  “test_04.jpeg”  GPLCD came up just fine using the “Default” option.  Windows in one NTFS primary partition, Linux wrapped up in an extended partition.  This is the original laptop HDD.  It came from Acer with 4 primary partitions.  First thing I did after buying the laptop was make the recovery DVD's.  Second thing I did was break Vista.  I ran the recovery DVD's and the original partitions disappeared, replaced by one monolithic NTFS partition.  From there it was relatively simple to install Ubuntu.  The laptop has 2GB RAM so I should have made swap at least 2 GB.

Test #5:  same Acer 5920 laptop, with a 7200 rpm 320GB HDD in place.  It only takes a few minutes to swap HDD's and I wanted to see if a 7200 rpm drive made a noticeable difference.  It does feel snappier.  / is in a primary partition, swap and /home in extended “box”.  

Test #6:  a Dell 470 Xeon workstation.  I didn't have a SATA HDD handy when I set this thing up so it's running off the PATA bus.  Notice the drive is recognized as “hda”, not “sda”.  This is another dual-boot (XP/Jaunty) but this time Linux / is in a primary partition, rather than inside the extended as in test #4.  If there is a “classic” dual-boot this is probably it.  Putting the Linux OS in a primary partition works just as well as inside the extended partition.

I hope this helps some of the folks who want to install Ubuntu but are put off by partitioning questions.
Screenshots are easier from the UCD, but not all that hard from GPLCD.  If you get a blank screen with GPLCD, hold down the power button until the PC stops, then start again and try some of the other options.

Take a good look at the dual-boot shots and compare them to the single-boot shots.  You should be able to see some patterns.  Notice that Linux puts a hold on the first four partition numbers.  It doesn't matter if there are one or two or three primary partitions - the logical partitions always start with “5”.

Make your swap a little bigger than your physical memory if you want to use “suspend”.  

Dangit, I can only upload 5 .jpeg's at a time, so will have to add a post to plug in the 6th screenshot.

---

### Post by Bartender on 2009-08-25
Here's the Dell 470 screenshot, test_06.jpeg

It'd be great if some other folks posted screenshots of their installs, along with any comments about what was involved! :)

---

### Post by Bartender on 2009-10-08
UPDATE:  I've never been exactly clear on what gets mounted when using an Ubuntu LiveCD vs. GPLCD.  I had believed that / *and* swap are both mounted when using an Ubuntu LiveCD.  
After discussing this with duncan, a co-conspirator and friend on these forums, we both ran some tests.
Turns out that only swap is mounted, and that's easily fixed by right-clicking on swap and choosing the "swapoff" option.
We both manipulated / partitions from within Ubuntu LiveCD's.

I still prefer the stand-alone GPLCD, but I wanted to add our findings to this post.

---

### Post by philinux on 2009-10-08
> **Bartender said:**
> UPDATE:  I've never been exactly clear on what gets mounted when using an Ubuntu LiveCD vs. GPLCD.  I had believed that / *and* swap are both mounted when using an Ubuntu LiveCD.  
After discussing this with duncan, a co-conspirator and friend on these forums, we both ran some tests.
Turns out that only swap is mounted, and that's easily fixed by right-clicking on swap and choosing the "swapoff" option.
We both manipulated / partitions from within Ubuntu LiveCD's.

I still prefer the stand-alone GPLCD, but I wanted to add our findings to this post.

Yep swapoff does the trick. With the live cd you have access to the net hence FF and things like testdisk can easily be installed, or any other software you might need.

---

### Post by LewRockwell on 2009-10-08
Puppy Linux LiveCD and Parted Magic LiveCD both have Gparted also

Some *nix live distros automatically mount any available swap and others don't

The difference seems to be whether or not the distro is designed for "ease of use" or for "forensic" purposes

Modifying boot parameters manually at boot time may work for some distros

We much prefer to use light/very-light live distros when we're hacking around, as opposed to the bloatware distros

As always, your mileage may vary...buyer beware and buyer be aware...

.

---

### Post by LewRockwell on 2009-10-08
> **philinux said:**
> Yep swapoff does the trick. With the live cd you have access to the net hence FF and things like testdisk can easily be installed, or any other software you might need.

Parted Magic has many utilities including Testdisk, Photorec, and Gparted as well as network/internet/browsers

.

---

### Post by _duncan_ on 2009-10-08
GParted Live CD, Ubuntu Live CD, Puppy Live CD, Parted Magic are all good tools. They offer a varied range of capabilities/features, on top of the capability to fully partition hard drives.

A major consideration though is how much RAM the computer has. This is particularly important if the user intend to use the Ubuntu Live CD on a computer with modest RAM size. By modest I mean 384 MB or lower.

By disengaging the swap partition using the "swapoff" option, the user is basically telling the Ubuntu Live CD not to use swap space in case it runs out of RAM to support its processes. This could pose a major problem for computers with low RAM size. In this case, using the other options mentioned may be the best course of action.

---

### Post by Bartender on 2009-12-20
UPDATE:
Just downloaded and burned the latest version of GParted LiveCD (0.5.0-3).  It ran automagically on the P5GDC-V described in first post.  The fussy one that required "Forcevideo".

Open source is so cool.  If something doesn't work, wait for the next version and try again!

---

