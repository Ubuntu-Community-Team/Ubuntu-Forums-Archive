---
title: "No Root File System Defined"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by A-beginner on 2010-01-15
I have a problem with installing ubuntu. When I install it outside or inside windows I get this error message: '**No root file system is defined. Please correct this from partitioning menu'**.
 
 
When I do installing inside windows this message comes after rebooting the computer. In this case, no matter how many times I click 'OK'. The message always comes back. Usually I had to shut the computer to reboot. 
 
 
When I do installing outside window I can reach step 4 of 7. At step 4, the page is white and **NO** menu is active. When I click froward to go to step 5 of 7, again I get the same error message: . **No root file system is defined. Please correct this from partitioning menu.'**
 
 
My computer made up of 0.5tb HD, 775 socket mother board and core2 cpu. Please help.
 
 
My overall assessment as a beginner with ubuntu is that it is a lot better than windows. Once I succeeded to install it when I got two new 0.5tb hd to raid my computer. When I tried to install ubuntu first after raiding my computer, the installation went on successfully in a short time. It installed drivers for all other components including graphic cards and sounds. Reinstallation of WinXP took long time and I had to reinstall drivers for every components. I have p5n-d motherboard with realteck-HD-audio, the drivers of which now always fails to load. But this didn't happen with ubuntu. Simply ubuntu made it operational without loading the diver.

---

### Post by Paqman on 2010-01-16
Your doing manual partitioning yes?

You need to pick the partition that you want to install Ubuntu on and give it the mount point / (pronounced "root"). You'll also need to create a small swap partition (formatted "swap", no mount point).

---

