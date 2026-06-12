---
title: "Help with WD Elements external disk"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by daveli on 2011-01-04
Hello!

Previously I had a "WD Essential" and when plugging it in, it would be automatically detected as My Book using the icon for external drivers on the toolbar, and when clicking on it it is properly mounted and can be accessed. I am now trying to access a new "WD Elements" hard disk for read/write. When I plug it in, the icon detects it as "Elements" but when I click on it my "Documents" directory is opened instead of the actual disk. Can anyone help me? I have searched through the web for info but most of it relates to using commands and I easily get lost. I looked at the /media directory but although I see the "My Book" disk, this does not show the "Elements" disk, I guess because it has not been mounted.

Using Dolphin to see the directories and navigating to root, I see "Elements" but when clicking on it I get an error saying "Failed to read last sector (3907027119) Invalid Argument...Hints: Either the volume is a RAID/LDM but it wasn't setup yet, or it was not setup correctly, o a wrong device is tried to be mounted, or the partition table is corrupt (NTFS size is not valid), or the NTFS boot sector is corrupt (NTFS size is not valid). Failed to mount '/dev/sdc1': invalid argument. The device '/dev/sdc1' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?"

How can I access it? I know the format of the disk is NTFS and I don't think I should change it since the disk will also be used on windows machines.

Please write slow as managing my kubuntu is taking me ages!

Thanks for your help, it is greatly appreciated

D.

---

### Post by cariboo on 2011-01-04
Hook the drive up to a Windows system, and run chkdsk on the drive.

---

### Post by psusi on 2011-01-04
For some reason WD is shipping these drives with a broken format.  Repartition and reformat the drive.

---

### Post by daveli on 2011-01-05
Thanks for your help. While waiting I tried reformatting the disc using a windows machine (as psusi suggested later on) but after waiting for a day (2Tb disk) the program now says that the disk could not be formatted. Now I cannot even access it using Windows. I tried using the chkdsk option suggested by cariboo907 but the cmd console would not change into the F: unit where it was hooked to. I am trying again with the formatting option but I am afraid that the formatting will fail again. 

Can you suggest anything I can do?

Cheers,

D.

---

### Post by psusi on 2011-01-05
You don't change to the drive to check it, just run chkdsk /f f:

Also you need to repartition before formatting.

---

### Post by colin.p on 2011-01-05
> **daveli said:**
> Thanks for your help. While waiting I tried reformatting the disc using a windows machine (as psusi suggested later on) but after waiting for a day (2Tb disk) the program now says that the disk could not be formatted. Now I cannot even access it using Windows. I tried using the chkdsk option suggested by cariboo907 but the cmd console would not change into the F: unit where it was hooked to. I am trying again with the formatting option but I am afraid that the formatting will fail again. 

Can you suggest anything I can do?

Cheers,

D.

Try this [http://community.wdc.com/t5/Other-Externals/2TB-WD-Elements-HD-can-t-reformat/td-p/37535](http://community.wdc.com/t5/Other-Externals/2TB-WD-Elements-HD-can-t-reformat/td-p/37535)

or this [http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=3865&p_sid=7lPkhljk&p_lva=5482&p_accessibility=0&p_redirect=&p_srch=1&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzMsMzMmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWVsZW1lbnRz&p_li=](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=3865&p_sid=7lPkhljk&p_lva=5482&p_accessibility=0&p_redirect=&p_srch=1&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzMsMzMmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWVsZW1lbnRz&p_li=)

---

### Post by daveli on 2011-01-07
Great help Thanks! I did not know I had to re-partition before formatting. 
Thanks to all of you.

D.

---

