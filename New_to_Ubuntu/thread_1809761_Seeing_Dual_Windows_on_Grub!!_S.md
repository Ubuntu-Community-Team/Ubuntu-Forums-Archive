---
title: "Seeing Dual Windows on Grub!! :S"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by SuchetBargoti on 2011-07-22
Just installed Ubuntu, and its been a confusing ride. Lots of re installing done due to stupid errors.

During the journey, I ended up installing EasyBCD in Windows 7 to get the computer to boot straight to windows after I had formatted the Linux partition (trying to re-install Ubuntu 11.04). Anyways I believe I fudged something up somewhere.

Upon re-installing Ubuntu (which works well apart for some graphic card driver problems (which is a whole another [topic]("http://ubuntuforums.org/showthread.php?t=1808410&page=4")) Now In the grub menu, op top of the normal Ubuntu options, I have **_two_** lots of Windows:
```

Windows 7 (loader) (on /dev/sda2)
Windows 7 (loader) (on /dev/sda3)

```

Selecting sda3 starts up windows normally and I am happy
Selecting sda2 goes to another boot manager giving me the options between 
```

Windows 7
Microsoft Windows 7

```
I can select either of them and they both lead me to the normal windows 7 as above. Note: all files, folders, applications, settings etc are the same on windows from any of these options, I am pretty sure there is only one copy of Windows installed.

Overall I am happy to leave these two copies as they are and just select sda3 each time i need to load onto windows. This is a new computer, and I am just curious if I am going to experience any problems in the future due to this issue. If so, how do I get rid of this multiple boot options which seem to lead to the same thing.

---

### Post by coffeecat on 2011-07-22
The os-prober script looks for boot files in each partition when update-grub is run in order to decide which partitions to set up menu entries for. I guess it's found Windows boot files in both sda2 and sda3. Normally, it would only find boot files in the Windows 7 100MB boot partition (which *might* be sda2 in your case). I wouldn't be surprised if the boot manager menu you get when selecting sda3 is something to do with EasyBCD. EasyBCD has probably written something to the boot sector of sda3 and this has caused grub to create a menu entry for this partition - probably. :)

If you want to see what is actually going on, go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of your RESULTS.txt file in code tags for clarity.

The simple and pragmatic solution is to ignore your sda3 menu entry. If you are really keen to remove it, you would have to disable os-prober and create a custom grub entry in your /etc/grub.d/40_custom file. I can help you with that if you want when you've posted your RESULTS.txt file.

---

### Post by SuchetBargoti on 2011-07-22
> **coffeecat said:**
> The os-prober script looks for boot files in each partition when update-grub is run in order to decide which partitions to set up menu entries for. I guess it's found Windows boot files in both sda2 and sda3. Normally, it would only find boot files in the Windows 7 100MB boot partition (which *might* be sda2 in your case). I wouldn't be surprised if the boot manager menu you get when selecting sda3 is something to do with EasyBCD. EasyBCD has probably written something to the boot sector of sda3 and this has caused grub to create a menu entry for this partition - probably. :)

If you want to see what is actually going on, go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of your RESULTS.txt file in code tags for clarity.

The simple and pragmatic solution is to ignore your sda3 menu entry. If you are really keen to remove it, you would have to disable os-prober and create a custom grub entry in your /etc/grub.d/40_custom file. I can help you with that if you want when you've posted your RESULTS.txt file.

The second boot manager I get is from sda2 not sda3. 
I have added the results.txt [here]("http://paste.ubuntu.com/649891/") for you. 

I am very much a computer noob so I hope this process would not be too difficult to follow. Does it pose any harm on my currently installed Ubuntu or Windows? I don't mind leaving it as it is, I was just worried that it might pose problems sometimes down the track. Also if I was to leave things as they are now, does it make a difference which option i select to boot?

---

### Post by Quackers on 2011-07-22
I would suggest just using the sda3 entry.
The sda2 entry is picking up Windows boot files which are present in the recovery partition. This is normal.
The second boot manager is doubtless EasyBCD's.

---

### Post by SuchetBargoti on 2011-07-22
> **Quackers said:**
> I would suggest just using the sda3 entry.
The sda2 entry is picking up Windows boot files which are present in the recovery partition. This is normal.
The second boot manager is doubtless EasyBCD's.

Sweet, thanks for your input!

---

### Post by Quackers on 2011-07-22
You're welcome :-)

---

### Post by YesWeCan on 2011-07-22
Hi there. Your config is a bit upside down by the way. You have Windows and Ubuntu on separate disks which is very good, but you lose the booting benefits by having the Grub boot code on the Windows disk and the Windows/standard boot code on the Ubuntu disk.

If it works it works, but personally I'd sort this out to avoid future problems/confusion. :)

Disconnect the Ubuntu disk. Boot from Windows CD and use repair to reinstate the proper MBR. then disconnct the Windows disk and reconnect the Ubunu disk. Boot off the Ubuntu CD and use it to install the Grub MBR to that disk:
sudo fdisk -l
To check the drive letter of the ubuntu disk, was sdb might now be sda. Use the right one...
sudo  mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

Then set sdb (the ubuntu disk)  to be the first boot device. Boot ubuntu then run
sudo update-grub
To add Windows to the grub boot menu.

---

