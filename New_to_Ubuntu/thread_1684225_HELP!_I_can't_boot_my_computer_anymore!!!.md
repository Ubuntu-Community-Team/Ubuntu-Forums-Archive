---
title: "HELP! I can't boot my computer anymore!!!"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by percussionman11 on 2011-02-08
Here's the long and short:

I have 3 HDD's (1 Windows 7 OS, 1 Windows 7 Extended Partition, and one that was empty)

I decided to load Ubuntu on my third HD last night. This is when things went wrong...

The install went well (off of a LIVE USB disk), however I noticed that GRUB did not show up on the restart. I tried to restart again and realised that it was no coincidence the first time. So I was being forced into Ubuntu with no option for Windows.

I found a few web posts and tried to resolve from there (the post for the ubuntu fix is listed here simply for reference so you can see what I did:)

[www.webupd8.org/2009/12/how-to-recover-grub2-linux.html]("http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html")

(I made sure to use the correct partition when mounting which was sdb1)

After doing that I tried booting to my Windows 7 disk and repairing via console. The commands I used were: 

bootrec /fixmbr
bootrec /fixboot

I also attempted to use several of the options in bootrec (thanks to the /help command)

after doing a few changes I restarted my computer only to realise I now couldn't boot to Windows OR Ubuntu.

I kept getting the error "BOOTMGR is Missing". I found this article to help:

[www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/]("http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/")

First, I didn't see any of my OS in the System Recovery Options listed under Operating System (not sure if this is a bad thing.... but I know my files are still there as I did not mess with them, only the boot files).

Second, I attempted the "Startup Repair" which completed successfully but after a reboot still got the "BOOTMGR is Missing" error.

Finally, I attempted to do the command prompt "bootrec /fixboot" which I kept getting an error instead of the result listed ("The operation completed successfully").

I also have tried unplugging the HDD that I installed Ubuntu on with no change in problems.

[COLOR=Red]Suggestions would be GREATLY appreciated as I am completely down and out right now on my computer....thanks in advance.[/COLOR]

---

### Post by percussionman11 on 2011-02-08
[http://ubuntuforums.org/archive/index.php/t-542660.html](http://ubuntuforums.org/archive/index.php/t-542660.html)

Found this post and one of the last posts states: 

I hope I am not too late. I just had this type of problem when I installed Grub with opensuse 10.3. My system is a Toshiba A215 S4767. I got things working again when I slowed down to think about it. Toshiba has a hidden partition for its own file. Well long story short, the partition table from the opensuse install was broke. I booted the Vista disc, went to the command prompt, ran diskpart, made the toshiba partition inactive, made the vista partition 'active', then I did the bootrec /fixmbr bootrec /fixboot. All is now working. If I am too late, maybe this will help someone later before they think their system is hosed. I will still try a dual boot with Gutsy when it comes out. Vista is Ok, but it seems everything has to be done the hard way. M$ really worked on this one.



seems this would work but I don't know how to use diskpart. I have it opened (so it works still) but don't know how I would go about separating the partitions as mentioned above.

My computer has the WIN7 OS on one HDD and an extended partition on the other. This was the print out when I did 

"list disk":

Disk ### Status            Size       Free           Dyn   Gpt
-------- ---------------   --------   -------        ---   ---
Disk 0    Online            465 GB     0 B
Disk 1    Online            465 GB     0 B
Disk 2    No Media            0  B     0 B


"list volume":

Volume ###  Ltr  Label        Fs    Type       Size      Status  
----------  ---  ------------ ----- ---------- --------  -------
Volume 0     E    GRMCPRXFRER UDF   DVD-ROM    3075 MB    Healthy
Volume 1     C                NTFS  Partition   465 GB    Healthy
Volume 2     D                NTFS  Partition   465 GB    Healthy
Volume 3     F                      Removable     0 B    No Media


I currently do not have the Ubuntu drive plugged in.

A step by step would be GREATLY appreciated as I do not want to screw up my files, bad enough I screwed up the boot...

---

### Post by percussionman11 on 2011-02-08
using a USB with Ubuntu on it I opened GParted. I changed which HDD was marked for boot and which was inactive, by doing so my Windows Recovery recognized the Recovery files. The result, windows fixed itself and I was able to boot.

---

