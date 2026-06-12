---
title: "Installation woes"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by KarenAK on 2009-04-23
a few days ago I installed ubuntu on my  brand new hp pavilion dv7 X64 Win Vista laptop - or I thought I did.  I have to admit that it took me a few days to realize that Ubuntu had installed itself on my external USB hard drive - probably because there was the most free space. I was just happy that it was working at all and didn't bother to check the hard drives (*blush)  So I bought a second USB hard drive and am currently saving my data onto that new one before I kill the partition and reformat the drive.  Here is my question:  What about the bootloader ? Will Windows be able to start once I kill the partition ?  I intend to install the new ubuntu version - this time on my c: drive.   Should I leave the first Ubuntu installation intact and only disconnect the USB drive before the installation of the new version ? Just in case ?  Does anybody have any recommendation regarding what I should do in what order ?  Anything else I ought to consider / do / avoid doing ?  Any help / suggestion is much appreciated.  Thanks in advance,  Karen

---

### Post by LowSky on 2009-04-23
whats a C: drive?


just kidding, we dont use those Windows term in the linux world, please from now on call it a hard drive.

as for the boot loader, You can easily find out where is was installed. unplugg the external drive and boot the machine, if Grub pops up and with an error then its on your master internal hard drive (ahem... c drive), if not, the boot loader is on the External and windows will boot fine. if not then you will need to revoer the windows MBR, simply done with a windows (I hope you have one) recovery disc.

---

### Post by card_ace on 2009-04-23
i'd recommend booting from the cd and removing your external usb drive.  personally i have my ubuntu on my external, but if you'd rather have it on the internal drive then simply take out the external when you reach the partitioning stage of the installation.  or just don't put it in until after the installation is complete.  as long as the external isn't in i think the bootloader will be installed to the MBR of your internal disk.  is windows installed on the internal or external disk?

---

### Post by KarenAK on 2009-04-23
Yes, Windows is on the c: drive and yes, I do have a recovery CD but I would sincerely hate to use it because it took me days to setup my windows apps just the way I like them. If I could switch over to linux completely, I would do it. However, I would lose all my audible audiobooks and that is not an option. 

Question:

When I install Ubuntu on the laptop hard drive won't it replace the existing bootloader (provided that it IS on that drive, I'll test it as soon as my data has been saved) with a new one ?

---

### Post by Madhatter14641 on 2009-04-23
Luckily, if your MBR is all messed up, you don't have to completely restore to fix it. 

If you have a windows install disc (or an upgrade anywhere disc), boot into it, go into the repair console (I think the key is 'r' when it finally gives you a menu, but don't hold me to that), and type in "bootrec /fixmbr". Details on bootrec can be found here: [http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392"). 

If you don't have a windows installation disc (or if you only have the HP recovery dvd's), you can get a repair disc [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). Keep in mind that these are for repairs only- you can't install from them, even though the option is there. Make sure you grab the 64 bit one!

Hope this helps. =)

Oh- and the new installation will add a new bootloader. Make sure you fix the MBR first though!

---

### Post by KarenAK on 2009-04-23
Thank you - that was very helpful indeed !

---

### Post by KarenAK on 2009-04-24
The Windows recovery CD worked like a charm. It went back only one day - so everything is still here. 


Now all I have to do is find the courage to give it a second try......:-)


Thanks again for the help !

---

