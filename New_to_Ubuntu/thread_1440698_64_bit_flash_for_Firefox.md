---
title: "64 bit flash for Firefox"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by MisFitt on 2010-03-27
On a clean install of Jaunty 64 bit I'm having a problem with flash.
I've screwed the installation somewhere e.g.:you tube videos just have a little flash/play logo which,when clicked,play perfectly but it's not right,they're not just "there".
I tried the instructions here,twice and it hasn't worked
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)
help!
I have spent 2 days moving files,partitions and hard drives around,chkdsks,prayer to get my system going.
(I can purchase new hard drives in about ten days)
I know the obvious damage that can occur with wear etc but I'm quite surprised that my
500GiB 2 year old HD is possibly failing.
I have been dual booting xp and have had viral...bad,bad meltdowns,one even immediately after connecting to the net after install and one BEFORE so I'm Jaunty only while I sort files and await equipment.What kind hard drive problems can occur due to virus/hacking etc that can appear as physical damage?
Thanks

---

### Post by NightwishFan on 2010-03-27
Uninstall and reinstall flash. I use flash from a PPA, but none of the ones I use are for Jaunty. Also perhaps download the official 64-bit flash, uninstall the deb on Ubuntu, then copy the .so file to /usr/lib/mozilla/plugins

---

### Post by audiomick on 2010-03-27
Hi MisFitt.
Use this link out of the thread you linked to for unistalling.
[http://ubuntuforums.org/showpost.php?p=8666948&postcount=72](http://ubuntuforums.org/showpost.php?p=8666948&postcount=72)
I did that before running the script, and it worked well for me.

I don't know if viruses can physically harm a drive, but it may be that your drive is dying a "natural" death. Sometimes you get a dud that just makes it through the warranty period...
Have you tried running smartmontools on it?
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by MisFitt on 2010-03-27
Thanks,I did it only to find the same thing happenning,hmmn

---

### Post by MisFitt on 2010-03-27
Bizarrely in synaptic manager there was flashblock enabled-I only found out by watching a you tube video,all fixed after removing yet I didn't install it in the first place!?

---

### Post by MisFitt on 2010-03-27
> **NightwishFan said:**
> Uninstall and reinstall flash. I use flash from a PPA, but none of the ones I use are for Jaunty. Also perhaps download the official 64-bit flash, uninstall the deb on Ubuntu, then copy the .so file to /usr/lib/mozilla/plugins
Hi and thanks.
This code is beyond my knowledge at this point.
I don't know how to execute it,yet

---

### Post by tom.swartz07 on 2010-03-27
> **MisFitt said:**
> Hi and thanks.
This code is beyond my knowledge at this point.
I don't know how to execute it,yet

Follow the x64 Flash link in my signature and it will show you how to do exactly that. :D

Good luck!

---

### Post by MisFitt on 2010-03-28
> **audiomick said:**
> Hi MisFitt.
Use this link out of the thread you linked to for unistalling.
[http://ubuntuforums.org/showpost.php?p=8666948&postcount=72](http://ubuntuforums.org/showpost.php?p=8666948&postcount=72)
I did that before running the script, and it worked well for me.

I don't know if viruses can physically harm a drive, but it may be that your drive is dying a "natural" death. Sometimes you get a dud that just makes it through the warranty period...
Have you tried running smartmontools on it?
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
Smartctl open device: /dev/sda failed: Permission denied
computer@computer-desktop:~$ sudo smartctl -a -d ata /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD5000AACS-00G8B1
Serial Number:    WD-WCAUK0106989
Firmware Version: 05.04C05
User Capacity:    500,107,862,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Mar 28 17:46:36 2010 EST
SMART support is: Available - device has SMART capability.
SMART support is: Disabled

SMART Disabled. Use option -s with argument 'on' to enable it.
computer@computer-desktop:~$ 

that's all I have thus  far and I'm not sure about it
just tried more,to enable and got:
smartctl -s on /dev/sda 
Smartctl open device: /dev/sda failed: Permission denied

---

### Post by tom.swartz07 on 2010-03-28
> **MisFitt said:**
> Smartctl open device: /dev/sda failed: Permission denied
computer@computer-desktop:~$ sudo smartctl -a -d ata /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD5000AACS-00G8B1
Serial Number:    WD-WCAUK0106989
Firmware Version: 05.04C05
User Capacity:    500,107,862,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Mar 28 17:46:36 2010 EST
SMART support is: Available - device has SMART capability.
SMART support is: Disabled

SMART Disabled. Use option -s with argument 'on' to enable it.
computer@computer-desktop:~$ 

that's all I have thus  far and I'm not sure about it
just tried more,to enable and got:
smartctl -s on /dev/sda 
Smartctl open device: /dev/sda failed: Permission denied

use the command gksudo before the terminal command and it should work. whenever you get a permission denied alert, that means you should use the sudo command.

---

