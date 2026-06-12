---
title: "ubuntu not booting up after update 10.4 (lucid lynx)"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by suneil9 on 2010-10-25
Hi,
I have been using lucid lynx for some months with no problems, and a few days ago ran some updates. After running the updates, ubuntu re-booted fine the first time. However, after a second reboot, it now hangs on the purple screen. The purple screen still has the moving dots. When I press escape at this point (to access the 'black' screen behind) i could see that it had frozen at this point where is says the following:
 
*starting TiMidity++ ALSA midi emulation*
*Home directory /etc/timidity not ours*
 
 
therefore, I tried to change the permissions on the timidity folder to 444 and 777, but this had not helped.
 
At the moment, it now hangs at the point where it says something like:
 
*checking battery status*
 
I have also tried to remove timidity and re-install it with the following commands:
 
*sudo apt-remove timidity*
*sudo apt-get install timidity*
 
I have also run the commands:
 
*sudo apt-get update --fix-missing*
 
 
I have also tried to load the GUI by typing
*sudo X*
 
 
which just hangs on a black screen.
 
I was thinking to try a liveCD, and maybe atleast I'd be able to access my files, and back them up. At the moment, I can't even mount a USB stick in recovery mode to back up my files. 
 
Aside question: If I did another liveCD install, would it overwrite all my existing installed programs?
 
 
Any help will be most appreciated. I don't know anything about log files, so if there is something I can post from a log file, perhaps that should be investigated. 
It may not have been the update that has triggered the crash, but I can't think what else it may be. I had also installed some encryption on a folder a few weeks ago, called Encfs (i think) but I think this is unrelated to the crash.
 
 
Many thanks in advance
 
Suneil

---

### Post by bioterror on 2010-10-25
> **suneil9 said:**
> 
I was thinking to try a liveCD, and maybe atleast I'd be able to access my files, and back them up. At the moment, I can't even mount a USB stick in recovery mode to back up my files. 
 
Aside question: If I did another liveCD install, would it overwrite all my existing installed programs?
 
 
Any help will be most appreciated. I don't know anything about log files, so if there is something I can post from a log file, perhaps that should be investigated. 
It may not have been the update that has triggered the crash, but I can't think what else it may be. I had also installed some encryption on a folder a few weeks ago, called Encfs (i think) but I think this is unrelated to the crash.
 
 
Many thanks in advance
 
Suneil

Sorry to hear that your upgrade didnt go that well.
But I can answer that if you have enough space on your system, you can install two Ubuntus side by side. There's an option for that. You cannot install it over the current installation, becouse you will loose all your files.

Best option is to boot LiveCD, make some backups (maybe to external usb hdd or stick or what ever you might have near you) and and make a clean installation.

---

