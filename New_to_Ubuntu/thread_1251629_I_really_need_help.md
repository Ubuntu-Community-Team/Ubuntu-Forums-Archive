---
title: "I really need help"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by billthecat on 2009-08-27
HP nc6000 laptop
1Gb ram
40Gb harddrive
 
Hi,
I cannot figure this out, last week I did a clean install of ubuntu 5.10 ( I have both disks ) on to my laptop, then I upgraded ubuntu to version 9.04 
this worked fine until I needed to run a program called retail Q 4 (iqmetrix). I found out that this software will only run on winxp or vista... sadly I have to remove ubuntu.
ok.. this is where the problem starts....
I stuck my winxp disk in and rebooted.... would not boot from disk... ok
restarted, went into bios setup, saw that my boot options were either multibay or harddrive ( seems my bios is changed and not listing cdrom as an option).
I picked multibay as option first to boot then saved and rebooted, the laptop still did not read winxp and continued loading ubuntu.
I pulled the HD, formatted it back to NTFS on a different computer running winxp
re-installed the HD and again went into bios and selected multibay, then rebooted the comp with winxp in the drive... now I get GRUB Loading stage1.5
then Error 17... 
Does ubuntu change your bios?
I don't understand.... please help, I need thes comp for work on monday and I didnt expect this to happen.
thanks 
Scott

---

### Post by coldReactive on 2009-08-27
Get DBAN: [http://en.wikipedia.org/wiki/Darik%27s_Boot_and_Nuke](http://en.wikipedia.org/wiki/Darik%27s_Boot_and_Nuke)

And wipe the entire drive.

---

### Post by Villiam on 2009-08-27
Its really weird that your bios does not support cd-rom boot option. How did you install ubuntu in the first place? By disks you must be meaning CDs. Right?
As a possible solution you can check your laptop's manufacturer's site and download bios upgrade if available. Then you anyother working (bootable) harddisk and install the correct bios.

---

