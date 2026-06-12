---
title: "Step 4 - No Partitions - ubuntu 8.10"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by michael.693 on 2009-01-15
Hi guys,I have just tried to install ubuntu 8.10 on another computer, when i get to step 4 in the installation there are no partitions to select, when i select forward it says no root file system is defined pleace correct this from partition menu... 

How can i fix this to just install?

Thanks,
Michael.

---

### Post by LowSky on 2009-01-15
click on manual partition, and set up the partitions.

you need at leas 2 one for root and one for swap. my sugesstion is three: root, swap and home.

---

### Post by michael.693 on 2009-01-15
Where is the manual partition located?

---

### Post by swoody on 2009-01-15
The manual partitioner should be an option on the page BEFORE where you were told "No Root File System Detected" There should be an option for "Guided Partitions - Use entire disk" and "Guided Partitioning - Use Max Free Space" and then "Manual Partitioning" Select that one, and go on to the next screen where you create your partitions. A good rule of thumb is to have a '/' (root) partition that is ~10Gb, a 'swap' partition that is between the size of your RAM and double your RAM, and then the rest as '/home' partition.

*Edit: Sorry if that was confusing. I meant the last screen you select options on BEFORE this error comes up*

---

### Post by michael.693 on 2009-01-16
Hi, 
no manual partition comes up:confused: all that comes up is an error message saying that with ok down the bottom, when i press ok it takes me back to step 4:confused:
Thanks

---

### Post by swoody on 2009-01-16
What setup options are displayed on the screen that you're on before you get this message? It should be the "Prepare disk space" screen, correct? That is where you select "Manual" underneath "Guided - use entire disk" Is this the screen you get to? If not, what screen is the last one you can access before this error comes up?

---

### Post by k3lt01 on 2009-01-16
> **michael.693 said:**
> Where is the manual partition located?Read this [Ubuntu Help Page]("https://help.ubuntu.com/community/GraphicalInstall")

---

### Post by burnetbj on 2009-01-16
Hi there

The reason you are not able to see the hdd is it is in use. While booted in live CD go to places and unmount any partitions or hdd listed and yo should get a list again when you back into gparted on LiveCD side

---

### Post by k3lt01 on 2009-01-16
> **burnetbj said:**
> Hi there

The reason you are not able to see the hdd is it is in use. While booted in live CD go to places and unmount any partitions or hdd listed and yo should get a list again when you back into gparted on LiveCD side
How does that work? I was under the impression that inserting the LiveCD and restarting the machine so it booted from it automatically unmounted everything except for the LiveCD.

---

### Post by burnetbj on 2009-01-16
Booting from CD-ROM is just that, selecting the LiveCD OS as the first boot device. Has nothing to do with what partitions will be mounted or unmounted once you up. I could be wrong and it might be the other way around, in main menu go to places and then right click the listed partitions and select either mount or unmount. One of them will then bring up your normal list in gparteds partition setup either way it should make sense when you get there.

I am by no means trying to sound smart here as I am very green in Linux but I just went thru this last install I had on 8.10

---

### Post by k3lt01 on 2009-01-16
I have never had to do anything like that but it's probably worth a try for the OP.

---

### Post by michael.693 on 2009-01-16
> **burnetbj said:**
> Booting from CD-ROM is just that, selecting the LiveCD OS as the first boot device. Has nothing to do with what partitions will be mounted or unmounted once you up. I could be wrong and it might be the other way around, in main menu go to places and then right click the listed partitions and select either mount or unmount. One of them will then bring up your normal list in gparteds partition setup either way it should make sense when you get there.

I am by no means trying to sound smart here as I am very green in Linux but I just went thru this last install I had on 8.10

Hi thanks all for the help,
i have tried this but under places i cant see any partitions, what would they be names? there are just the usual things, also when i right click on them it just opens them up...

---

### Post by michael.693 on 2009-01-16
> **k3lt01 said:**
> How does that work? I was under the impression that inserting the LiveCD and restarting the machine so it booted from it automatically unmounted everything except for the LiveCD.

Hi thanks for the help,
i have also tried this and its the same.. nothing on the partition list...

---

### Post by k3lt01 on 2009-01-16
Have you got a floppy drive? If you have and have a Windows Boot Disk reformat the HDD to FAT32. After that try the Ubuntu Live CD.

Be very aware that if you do this all information on the HDD will be destroyed.

---

### Post by burnetbj on 2009-01-16
OK lets start over here

So you have you system setup to boot from CD first
You also have the LiveCD in the CD-ROM drive and the CD works OK
When you go to install, you are getting to the partitioning area but are not able to see any partitions listed to choose to format or edit. Am i correct so far?

once you are to this point stay in the LiveCD and go up top to the Applications-Places-System and choose Places. 
Under Places you should see a little HDD or hard drive icon and a number like Example mine is listed as (23Gb Media) this is my windows xp 
Theres also one called (ServiceV002) which is just a Vista recovery partition (Work laptop)

Trying to get you a screen shot but i cant seem to get a print screen while places is selected .....bummer

Should see this 

Home folder
Desktop
Documents 
Music
Picture
Videos
Computer
CD Creator
CD-ROM
then partitions
network 
then few others

This is just my Example 
Yours may be in a slight dif order

If there is nothing listed then i am assuming this is why there might not be a listed partition to choose from. Then we will need a pro to chime in here and help mounting your HDD
If this is a HDD you just installed please double check cables and BIOS settings that SATA or SCSI is enabled or what have you

---

### Post by michael.693 on 2009-01-16
Hi guys, i got it insalled finally:KS
but i decided to try and unplug the hd and stick it back in, not it comes up with operarting system not found, any idea why this is?

---

### Post by k3lt01 on 2009-01-16
well done michael.

---

