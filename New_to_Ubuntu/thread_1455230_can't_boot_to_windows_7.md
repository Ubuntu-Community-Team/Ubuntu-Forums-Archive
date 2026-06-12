---
title: "can't boot to windows 7"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by m1stikal on 2010-04-15
I know there are alot of these posts but i haven't found someone with quiet the same problem as I have.

I recently install ubuntu 9.10 after running windows 7 dual boot with windows XP. Ubuntu installed on its own new partition. After installing ubuntu 9.10 I used gparted to format the original partition on which windows XP was installed seeing as I had no more need for XP and needed the space. 

When i rebooted i got the grub menu and tried to boot the windows 7 loader but got the error error no such device. I tried sudo update-grub and it refreshed the menu items but did not find my windows 7.

I am absolutely sure i formated the right partition since i can still access my windows 7 files.

please help me...

---

### Post by undecim on 2010-04-15
Do you see an "ntldr" file on your Windows 7 drive? (I hope it hasn't changed since XP... I'll Google it)

---

### Post by frantid on 2010-04-15
In an XP win7 dual boot, win7 put's its boot loader in the xp partition.  You need to fix the win7 boot dirs and boot loader.  read these steps:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

you will then lose grub and have to run off the livecd to install grub back to the mbr.

If you have a backup or another win7 system, you could try to copy the c:\boot directory and the bootmgr file from the root of c:  -- then you might not have to go through the recovery steps and reinstalling grub.  They would have been in your xp partition.

---

### Post by m1stikal on 2010-04-16
Thanx alot that sorted it...

---

### Post by w-cdma on 2010-04-23
Hello all from New Zealand!


I've got what I think is almost exactly the same problem as the OP in this thread.

Basically I installed Ubuntu 9.10 to a separate partition so I could dual boot win 7 ulti and ubuntu.  This isn't the first time I've done this, however, this is the first problem I've had that I haven't been able to solve myself.  (I in no way profess to being even remotely skilled at ubuntu troubleshooting, most of the time I'm schmoozing through forums looking for my answer)

All was fine until I connected to the internet for the first time and downloaded all the package upgrades.  One of these was an update to the GRUB.  After this was run, Win7 was removed from my GRUB menu and as a result I can't boot into it.  This is a shame as there are a couple of windows specific applications that I need to run for work.

I've tried following some instructions I found in these forums however the OP's issue slightly differed from mine.  I've run a few terminal commands regarding editing the grub list (sorry if thats kind of vague I'm still trying to get my head around terminal) 

anyway, I'm really just wondering if any of the ubuntu boffins on this forum might have a few tips for me to try?  I really don't want to install windows again as there is some data on that partition that I would really like to hang on to.  I also no longer have the win7 DVD so I can't follow the steps that were linked in the post above mine.

Thanks for taking the time to read this and I look forward to your response (hopefully!)

---

### Post by ed-koala on 2010-04-23
See if this thread helps.

[http://ubuntuforums.org/showthread.php?t=1453700]("http://ubuntuforums.org/showthread.php?t=1453700")

It may be as simple as just adding Win 7 to your Grub list.

---

### Post by w-cdma on 2010-04-23
thanks mate, if it helps at all I find I can no longer mount sda2 (my windows partition) 


I will have a read of the thread and report back

thanks again

---

### Post by xumuk37 on 2010-04-23
Welcome at forum, w-cdma. It's a one of many typical bugs of update-grub... If all that you want is can boot windows press alt+f2 gksu /boot/grub/grub.cfg and add ```

 w7 on /dev/sdaX
menuentry "w7  on /dev/sdaX" {
    set root=(hd0,X)
        chainloader +1
        }

``` as os_prober for try...

---

### Post by w-cdma on 2010-04-23
oh, nothing happens when I do that?  what does gksu mean?

---

### Post by ed-koala on 2010-04-23
You really shouldn't edit grub.cfg itself, it isn't meant to be edited.

There are other files to edit that are used to create grub.cfg.  Those files are the ones in my thread.

---

### Post by w-cdma on 2010-04-23
ed_koala you little beauty!!  Working perfectly, thanks a lot mate, big help!


Thank you for your time xumuk

---

