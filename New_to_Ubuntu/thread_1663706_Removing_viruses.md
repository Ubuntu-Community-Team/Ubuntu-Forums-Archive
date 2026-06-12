---
title: "Removing viruses"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-01-10
hi everyone
   i have a ubuntu 10.10 installation cd.. is it possible to detect and remove any virus present in windows 7.?:confused::confused::confused::confused:. pls somebody help me.. actually my friends lapi is bugged by a virus and i have to somehow solve her prob.. so please help

---

### Post by Bucky Ball on 2011-01-10
This might be difficult as Linux won't recognise a Windows virus!

Having said this there could be software out there. Hopefully someone can chime in with a fruitful suggestion. ;)

---

### Post by vivek.pandey on 2011-01-10
> **Bucky Ball said:**
> This might be difficult as Linux won't recognise a Windows virus!

Having said this there could be software out there. Hopefully someone can chime in with a fruitful suggestion. ;)

there are a lot of ways i can remove the virus
...i can restore windows to some previous date 
...i can install an anti virus and scan the lapi
...i myself have kaspersky so i can scan her lapi by connecting to my own by lan wire and there ar e many such stuffs
 but i want to try out ubuntu cd.. the principle behind my thought is v can see all softwares installed in windows when we boot inside ubuntu so may be we can see the virus somewhere too..and can delete it..i dont know whether i am right or wrong in this approach but wanna give it a chance so please help me

---

### Post by alphacrucis2 on 2011-01-10
> **neo_aryan said:**
> hi everyone
   i have a ubuntu 10.10 installation cd.. is it possible to detect and remove any virus present in windows 7.?:confused::confused::confused::confused:. pls somebody help me.. actually my friends lapi is bugged by a virus and i have to somehow solve her prob.. so please help


Download the free version of malwarebytes antimalware from [www.malwarebytes.org](www.malwarebytes.org) via the Ubuntu live CD and copy the downloaded installer to the main Windows ntfs partition. Then reboot Windows in safe mode (f8 under Vista or XP very early in the boot sequence just after the BIOS post completes - I assume that Windows 7 is the same). Run the installer under Windows safe mode and let it complete a scan. Hopefully it will find and eliminate the nasties. Reboot windows again in normal mode and run the malwarebytes antimalware program again. Good luck.

---

### Post by lisati on 2011-01-10
As has been suggested, there are options available to help you remove Windows malware. 

On my server I use ClamAV to check incoming and outgoing emails.

AVG have a [rescue CD]("http://www.avg.com/us-en/avg-rescue-cd") which you'd [put on CD]("https://help.ubuntu.com/community/BurningIsoHowto") The last time I took a look at it (some months back), it seemed to be Linux-based bootable CD.

---

### Post by Bucky Ball on 2011-01-10
> **alphacrucis2 said:**
> Download the free version of malwarebytes antimalware from [www.malwarebytes.org]("http://www.malwarebytes.org") via the Ubuntu live CD and copy the downloaded installer to the main Windows ntfs partition. Then reboot Windows in safe mode (f8 under Vista or XP very early in the boot sequence just after the BIOS post completes - I assume that Windows 7 is the same). Run the installer under Windows safe mode and let it complete a scan. Hopefully it will find and eliminate the nasties. Reboot windows again in normal mode and run the malwarebytes antimalware program again. Good luck.

Cheers, lisati. Nice tip. I'm bookmarking that! ;)

---

### Post by bodhi.zazen on 2011-01-10
> **Bucky Ball said:**
> This might be difficult as Linux won't recognise a Windows virus!

Having said this there could be software out there. Hopefully someone can chime in with a fruitful suggestion. ;)

That is only partially true. Linux AV will recognize the viruses in the Windows partition. You then "remove' the viruses by deleting the files.

That I know, you can not fix registry problems with a Linux CD, so you are probably better off :

1. Identifying the problem, it may not even be a virus.

2. Figuring out how to best fix the problem from there.

---

### Post by vivek.pandey on 2011-01-10
> **alphacrucis2 said:**
> Download the free version of malwarebytes antimalware from [www.malwarebytes.org](www.malwarebytes.org) via the Ubuntu live CD and copy the downloaded installer to the main Windows ntfs partition. Then reboot Windows in safe mode (f8 under Vista or XP very early in the boot sequence just after the BIOS post completes - I assume that Windows 7 is the same). Run the installer under Windows safe mode and let it complete a scan. Hopefully it will find and eliminate the nasties. Reboot windows again in normal mode and run the malwarebytes antimalware program again. Good luck.

thanx for this solution here are some of my doubts..
1)..via ubuntu live cd...u mean i need to boot the lapi with ubuntu cd connect it 2 given link and download the anti malware?
2)..there is a problem with dual boot and f8...ever since both of us have installed ubuntu along windows f8 seems to have stopped working no matter how much we press f8 it doesnt work.it used to work wen ubuntu wasnt installed
3)..i m really sorry for being stubborn but i want to find and eliminate the virus using ubuntu cd only ..sorry for that

---

### Post by mlinux on 2011-01-10
If you installed dual boot, press F8 only after you selected boot to window and must be quick after selection.

---

### Post by jroa on 2011-01-10
I had avast! and AVG installed on a bootable Mint 9 thumb drive.  I could connect it to any computer that was capable of booting from a USB and scan the Windows partition from there.  Just keep in mind that the scan will take a long, long time.  I can't remember if either of these is available from the repos, though.  I think I had to install them myself.

---

### Post by vivek.pandey on 2011-01-10
> **alphacrucis2 said:**
> Download the free version of malwarebytes antimalware from [www.malwarebytes.org](www.malwarebytes.org) via the Ubuntu live CD and copy the downloaded installer to the main Windows ntfs partition. 

thanx for ur advise but y at all do i need to download the anti malware using ubuntu cd if i have to copy everything in windows y cant i directly download it through windows... another point is wat i intend is to use ubuntu cd as an anti malware and not some other softwares

---

### Post by alphacrucis2 on 2011-01-10
> **neo_aryan said:**
> thanx for ur advise but y at all do i need to download the anti malware using ubuntu cd if i have to copy everything in windows y cant i directly download it through windows... another point is wat i intend is to use ubuntu cd as an anti malware and not some other softwares

Some viruses mess with the windows hosts file to deliberately block access to antivirus vendors websites. You may find you can't access malwarebytes.org from the infected copy of windows.

---

### Post by baddnady23 on 2011-01-10
Check out this site:

[http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/]("http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/")

---

### Post by sammiev on 2011-01-10
> **baddnady23 said:**
> Check out this site:

[http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/]("http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/")

+1 Tried and tested! :)

---

