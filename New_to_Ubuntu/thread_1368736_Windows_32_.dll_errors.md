---
title: "Windows 32 .dll errors"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Jas_India on 2009-12-31
Hi, i installed Ubuntu 9.10 from a Live CD on my existing Windows XP - Professional Edition, having 80 GB Hard disk. I installed it using within Windows option, allowing it to use 20 GB from my D drive. The dual boot worked perfectly fine for a day and since i was missing a software called mp3mymp3 installed on XP, i tried to install it in Ubuntu using the Wine utility. However there was some unexpected response and i had to shut down my PC. After i rebooted again and tried to boot in the Ubuntu from the start page, the screen hung and i got an error called: Windows 32.dll error. I switched off again and rebooted using Windows XP and to my great relief, i logged in XP. However, got the same message when i tried to boot into Ubunto. In a fit of rage, i decided to delete Ubunto from my system. I logged into XP, went to add/remove software and deleted Ubuntu. 
However, my problem now is, whenever i boot my pc, it again shows the dual boot option and hence i have to hit enter to boot into XP. The Ubuntu option shown is of no help to me as it is not working. 
After some time, i tried to install Ubuntu again using my Live, burnt CD. To my surprise, it failed to load. I inserted the CD during boot up now and clicked the option...check for integerity..it showed 18 errors.
Please tell me what is the way out for me.
Should i burn a new Ubuntu CD & take pains to load Ubuntu again? Or is there a safe & easy way to get rid of dual boot option? I do not have my orignal Windows XP Installation CD as it was loaded by a vendor. I can live without Ubuntu but if there is not much of hassle, i can attempt to load Ubuntu again on my PC.   
Many thanks in advance.

---

### Post by Temposs on 2009-12-31
Your CD may have gotten scratched without you realizing it, or something. You should make a new CD and try to install again. By the "within Windows option", do you mean that you installed Ubuntu with Wubi?

---

### Post by Jas_India on 2009-12-31
Hi, no i did not use the Wubi option. After i burnt the Live CD, it asked me for 3 options: Live demo, install within windows & something related to learning about Ubuntu. I went with the 2nd option as i did not want to mess my orignal XP partitions. Somehow, the chances of CD getting scratched appear bleak as i had kept it safely in a cover. Is it the only way out to get Ubuntu runing again or doing away with it? I am saying so as it is a pain to first downlaod 700 Mb of ubuntu installation and then burning it on a CD. I think i have also deleted the orignal ubuntu ISO image file from which i burnt the Live CD. Please help.

---

### Post by lindsay7 on 2009-12-31
[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)



How To Repair the Master Boot Record In Windows XP

By Tim Fisher, About.com Guide
See More About:

    * master boot records
    * fixmbr
    * boot sectors
    * windows xp recovery console
    * hard drive partitions

Repairing the master boot record on your Windows XP system is accomplished using the fixmbr command, available in Recovery Console. This is necessary when the master boot record has become corrupt due to a virus or some kind of damage.

Follow these easy steps to repair a damaged master boot record in Windows XP.
Difficulty: Easy
Time Required: Repairing the master boot record on a Windows XP system takes less than 15 minutes
Here's How:

   1.

      Enter Windows XP Recovery Console.
   2.

      When you reach the command prompt (detailed in Step 6 in the link above), type the following and then press Enter.

          fixmbr

   3.

      The fixmbr utility will write a master boot record to the hard drive that you're currently using to boot into Windows XP. This will repair any corruption or damage that the master boot record may have.
   4.

      Take out the Windows XP CD, type exit and then press Enter to restart your PC.

      Assuming that a corrupt master boot record was your only issue, Windows XP should now start normally.

---

### Post by Temposs on 2009-12-31
Hmm, I'd not seen that option before. Did you run the LiveCD within Windows when it gave you those options? If so, you probably did install with Wubi. I'm just trying to get a baseline of what you actually did to install Ubuntu. Pretty much the only way to install Ubuntu within Windows like you've described is with Wubi, I think.

A faster way to download the Ubuntu iso is to get the torrent, here(showing you both 32-bit and 64-bit):
[http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent)
[http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent)

---

### Post by Jas_India on 2009-12-31
Hi Temposs. I clearly remeber it was not using Wubi as i installed it using Wubi earlier. Somehow i skipped the step of assigning disk space to ubuntu and by default, it assigned some value. The installation with wubi fent fine but somehow i was getting the message that you are running low on disk space. I sought help from this forum and i was told that it is better to install using a Live CD. So, i uninstalled Wubi/ubuntu then reinstalled ubuntu from their website and burnt the ISO image on a blank CD (Live CD). I came to know that there are 2 options. If i insert the Live CD in a already running XP, it will show the 3 options that i mentioned earlier and if i inserted the CD during boot up..it will try to install it permanently in a new/existing drive. I do not know the technical difference between these options. So that's HOW i installed it. Now, i need to know....HOW TO MAKE IT WORK???

---

### Post by Jas_India on 2009-12-31
Hi Lindsay7, thanks for your help. But somehow i feel that as Windows XP is loading fine during boot up...ERROR is somewhere in Ubuntu boot loader. That is why i am not tinkering with my working XP. I may be wrong too as my knowledge of PCs is bare minimum.

---

### Post by MeTylerDurden on 2009-12-31
If you google windows run commands you will find a list and there you can find one to see your boot options and you can edit the list.. I have reinstalled ubuntu because of this before and always end up with a good reinstallation but always leaves the old ubuntu on the hard drive.. So I ended up reinstalling xp and ubuntu on other pc.. just because I could not get rid of the other one..and I downloaded my karmic 9.10 from a pc that runs only ubuntu..

---

### Post by lindsay7 on 2009-12-31
If you run the fixmbr command in the windows instructions, that will take out the grub dual boot function and you will only be able to boot into xp (no sign of Ubuntu). I would then use a Ubuntu live cd and use Gparted to reformat the partition where Ubuntu was.  Doing these things will get your computer back to were you started.  I would make sure that you have a good Ubuntu install cd burnt from the iso file and do the installation again.

---

### Post by Jas_India on 2009-12-31
Thanks lindsay 7. Sorry for asking a very basic question...but how to run the fixmbr command in the windows instructions. Should i type this in run? Also, is it necessary to use Gparted? I just do not want to see the ubuntu option in the boot up screen. I do not mind of it remains there, provided it does not affect XP functions. 
Also, if i back up my data on external drives and reload XP...Will it serve my purpose or will the Ubuntu resurface again?

---

### Post by Jas_India on 2009-12-31
Hi MeTylerDurden, the whole idea of installing XP & ubuntu all over again seems little frightening to me. Is there a quick - fix solution. I do not mind reloading Windows XP on my system again provided i get rid of ghosts of ubuntu. I think there is nothing wrong with ubuntu..it is a fab operating system. Somehow it can not co-exist with the more illustrious Microsoft XP. Wish i had read the consequences before installing ubuntu on my XP.

---

### Post by Temposs on 2009-12-31
Ubuntu can co-exist perfectly well with Windows XP. People do it everyday.

---

### Post by Jas_India on 2009-12-31
In that case, somehow things have messed up for me. Having burnt my hands once...do not want to take any risk again..................

---

### Post by Temposs on 2009-12-31
The most straightforward way to accomplish a clean install would be to reinstall Windows XP over everything, and then to install Ubuntu from the LiveCD, and on the partitioning step to choose to install Ubuntu side-by-side with Windows.

You can try the approach given by lindsay if you don't want to do what I have detailed.

---

### Post by MeTylerDurden on 2009-12-31
I usually end up doing a clean install of xp when problems arise but for the sake of saving all your stuff...   you can try this  Edit the Boot.ini File
To view and edit the Boot.ini file:

   1. Right-click My Computer, and then click Properties.
      -or-
      Click Start, click Run, type sysdm.cpl, and then click OK.
   2. On the Advanced tab, click Settings under Startup and Recovery.
   3. Under System Startup, click Edit.


also there is this to peruse:[http://www.ehow.com/how_5087860_fix-mbr-windows-xp.html](http://www.ehow.com/how_5087860_fix-mbr-windows-xp.html)

   I recall using the xp disc and recovery and reformating the hard drive that ubuntu was on to try and make it back to pristine condition and reinstall ubuntu so as to have one xp and one ubuntu.. it did not work out so good so ended up doing a clean install .. of both.. fresh is sometimes not so bad as it sounds..

---

### Post by Jas_India on 2009-12-31
Thanks MeTylerDurden! I will try this as a last resort & if things do not go my way...will have to re-install my XP. Will keep you posted on this......Have a Happy New Year 2010!

---

### Post by MeTylerDurden on 2009-12-31
they do work great side by side I have been running xp so I can use games that don't work with Ubuntu - so easy to install that you don't need to use a box of wrenches -  just remember to get all your updates  and upgrades in xp then install ubuntu side by side  and where you will use more hard disk space storing pictures or movies give that operating system (xp or ubuntu) more space in the partitioner..

---

### Post by Jas_India on 2009-12-31
It also looks like to fix the MBR, i have to use the orignal Windows XP CD. Unfortunately, i have to contact my vendor who installed it in the first place. Still, as i have a fair idea of what needs to be done, at least the vendor can not take me for a ride by saying things like..Windows need to be reloaded or hard disk needs to be changed. Thanks again.

---

### Post by candtalan on 2009-12-31
Welcome!

> **Jas_India said:**
> Hi, no i did not use the Wubi option. After i burnt the Live CD, it asked me for 3 options: Live demo, install within windows & something related to learning about Ubuntu. I went with the 2nd option
Although it does not actually say so, this is the install which makes use of the WUBI facility which is included in the live CD, so yes, you did a wubi install.
WUBI stands for Windows Ubuntu Installer.

I am sorry to hear you had problems. When you uninstalled Ubuntu after the first (wubi) install, you are left with the Windows boot manager still thinking Ubuntu is there. There is a simple edit in Windows to correct this, but even if you do not do the simple edit, your Windows will not be affected, you can continue to use it ok.

Also - when a live CD boots up (by itself, not in Windows this time), the initial menu includes a CD self check facility, which can be very useful. 
hth

---

### Post by Jas_India on 2009-12-31
Hi candtalan, i agree with you...i guess Ubuntu has got installed on my pc through wubi and somehow things have screwed up due to reinstall. Since i was not very sure about the best way to install and try ubuntu...this has led to my misadventure.
Anyways, what is troubling me know are 2 things:
1. Every time my PC boots up, i have to hit enter XP or else wait for good 18 seconds so that it gets booted up by default. (It is suicidal to wait so long in such fast running systems these days)
2. The PC boot up shows the option of ubuntu...which reminds me of this misadventure.
 
That is why..seeking help on this forum!

---

### Post by MeTylerDurden on 2009-12-31
[http://www.wikihow.com/Make-Windows-XP-Startup-Faster](http://www.wikihow.com/Make-Windows-XP-Startup-Faster)  you can change the boot xp screen time from 30 seconds to like 5 it  try - run -  misconfig  (sorry Im not using xp tonight  so dont know exactly but just recently changed the timeout option as you were requesting.  there is also this promising looking article.::[http://www.wikihow.com/Make-Windows-XP-Startup-Faster](http://www.wikihow.com/Make-Windows-XP-Startup-Faster)   :D

---

### Post by Jas_India on 2009-12-31
Sounds good! Will try it for sure.

---

### Post by Methuselah on 2009-12-31
The boot loader (that allows you to select an operating system) still thinks Ubuntu is there.
This is really a windows thing and I think someone posted information on how to fixmbr.

---

### Post by Jas_India on 2009-12-31
yes, this seems to be the only logical solution: fixing mbr. Thanks a lot..all of you

---

### Post by Jas_India on 2009-12-31
:P Finally......burnt a new LIve CD & reinstalled Ubuntu...All is well till now...this time installed it alongside my XP installation. THANKS ALL OF YOU FOR THE SUPPORT

---

