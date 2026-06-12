---
title: "Dual Boot System Problem"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by poscomp on 2011-05-21
I have been running Ubuntu for years. I just setup a new drive and put Windows 7 on 50% of the drive leaving 50% for Ubuntu 11.04. Both installs went as planned. When I rebooted the system it gave me an error message and would not run GRUB. I did it again with the same results. I then installed Ubuntu 10.10 on the Ubuntu partition and everything worked fine. Just as a lark, I did an upgrade to 11.04 and on reboot, the same thing happened. I reinstalled 10.10 and everything was fine. Currently I am running a dual boot system with Windows 7 and Ubuntu 10.10. Can anyone tell me how to get Ubuntu 11.04 to work? I have 2 notebooks and both run Windows 7 and Ubuntu 11.04 fine. ???????

---

### Post by Sidewinder1 on 2011-05-21
That's a "stumper", why 10.10 would work but not 11.04.
In 11.04 I guess you tried:
```
sudo update-grub
```
That's the only thing I can think of. :(

Side

---

### Post by oldfred on 2011-05-21
Is this a large drive. Perhaps one install vs. the other installed later in the drive and your BIOS settings are not set correctly.

It would be best to know exactly what error message was. And if you could run boot info script from system when it gives error.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

I saved these comments from others - see if any apply in your case:
It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.

---

### Post by poscomp on 2011-05-21
The error message is short and flashes by. Then I can't boot into either system until I loaded 10.10. It never touched my Windows partition. Both my other machines were upgraded and they both worked. I tried it with this machine and got nothing. 10.10 works fine.

---

### Post by bennachie on 2011-05-21
That's very interesting. If you have sufficient patience, could you install Ubuntu 11.04 again, and check that the problem is still there? Then reboot the system from a liveCD, open a terminal window, and enter the command:

sudo fdisk -l

That will show us the file systems installed on your hard drive.

---

### Post by poscomp on 2011-05-21
It installed on my hard drive, it just won't load grub. I can see all the data when I take the drive out, put it into an external case and view files from my notebook.

---

### Post by bennachie on 2011-05-21
Yes, I gathered that, but it would be good to know what exactly appears to be on the hard disk when viewed in situ in that machine which is giving you problems. A complete failure to install Grub is more than somewhat unusual, and we really do need to know what file systems the machine in question THINKS it is dealing with (as opposed to those which are seen through the prism of a notebook on which you have already been able successfully to install Ubuntu).

---

