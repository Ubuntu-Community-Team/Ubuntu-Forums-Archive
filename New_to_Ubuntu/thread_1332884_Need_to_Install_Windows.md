---
title: "Need to Install Windows"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by nnolund on 2009-11-20
Hey guys.

Got a bit of a problem. When I installed Ubuntu it was because my Windows partition got a pretty bad virus, and running Linux was the only way I could make it work. Ended up needing to use Wubi to get Linux installed, because my CD Drive was affected by the virus.

Now my Windows is COMPLETELY screwed (like, it won't load at all), but I want to reinstall it and dual boot Linux.

Does anyone know about a way to make it possible to install Windows (preferably XP Pro) from a USB drive? Every guide I have found has needed the command prompt, which I can't exactly use on Linux (and if I can somehow, I'd like to know that too).

Any help is greatly appreciated.

---

### Post by nazgulord on 2009-11-20
[http://linuxcommand.org](http://linuxcommand.org) is a great place to learn the command line. Hope it helps.

---

### Post by pbateman on 2009-11-20
I think (and I may be wrong but this is what I heard) that the only windows you can install from a Thumb drive is Vista or 7.....never tried it myself.
However thats really weird that a Virus would disable your CD Rom drive.

---

### Post by nnolund on 2009-11-20
> **pbateman said:**
> I think (and I may be wrong but this is what I heard) that the only windows you can install from a Thumb drive is Vista or 7.....never tried it myself.
However thats really weird that a Virus would disable your CD Rom drive.

The drive runs fine in Linux (it's not a burner though, which is why I need it on USB), but the virus literally destroyed everything on Windows (I can't even log into it anymore)

---

### Post by pbateman on 2009-11-20
Can you log into safe mode in windows? If you can I'd first try to download Malwarebytes (while in linux) then go into Windows safe mode and run Malwarebytes to see if it clears it.
Otherwise the easiest thing of course would be to try to get a hold of the original restore cd that came with the PC or a Windows CD and boot from that...

---

### Post by theozzlives on 2009-11-20
Viruses CANNOT infect hardware! Just use your Windows CD to put it back on. You can use Linux to recover your data first.

---

### Post by samigina on 2009-11-20
Boot from a Ubuntu Live USB, backup your data to and external hd or dvds, or whatever... then format your disk! and start from zero. I cant believe a virus has damaged your cd drive...

---

### Post by wilee-nilee on 2009-11-20
> **pbateman said:**
> Can you log into safe mode in windows? If you can I'd first try to download Malwarebytes (while in linux) then go into Windows safe mode and run Malwarebytes to see if it clears it.
Otherwise the easiest thing of course would be to try to get a hold of the original restore cd that came with the PC or a Windows CD and boot from that...
 +1 on the malwarebytes, there are many free AV programs that are superior to the big players in some areas, and don't run constantly using a lot of cpu.

---

### Post by neerajadsul on 2009-11-20
What I would suggest you is kinda summary of previous replies -
 1. Log into linux, copy all the important data from Windows (My Documents, Pictures, Videos etc. + if any data that you have on drives.) on an external drive. Do not copy programs and stuff which you can reinstall.

2. Then use bootable windows CD to boot, delete all paritions, format the drive completely and install the windows. While doing this remove external drive. Also while installing windows, please try to make two separate partitions.

3. After windows is completely installed, install antivirus, scan the data from the external drive.

4. Once you make sure that all data is fine, then install Linux. If your job/study doesn't depend on Linux, please try to focus first on the important data. (what I learned from my experience, or you loose huge amount of data.)

---

### Post by pi.boy.travis on 2009-11-20
> **pbateman said:**
> Can you log into safe mode in windows? If you can I'd first try to download Malwarebytes (while in linux) then go into Windows safe mode and run Malwarebytes to see if it clears it.
Otherwise the easiest thing of course would be to try to get a hold of the original restore cd that came with the PC or a Windows CD and boot from that...


This might not be the best idea.  Logging in, even in safe mode, will only do more damage.  I would recommend using the Ubuntu LiveCD (it will work regardless of the virus) top backup your data and then reinstall Windows with the CD that should have came with your computer.

---

### Post by nnolund on 2009-11-20
> **theozzlives said:**
> Viruses CANNOT infect hardware! Just use your Windows CD to put it back on. You can use Linux to recover your data first.

It wasn't the hardware that is infected. The drivers (along with everything else for that matter) on Windows no longer worked. The drive itself works fine in Linux.

My problem is that I don't HAVE a CD for Windows. The laptop I am using isn't brand new, and has no disc. I am borrowing it from a friend of mine, and they don't know where their disc is.

I would be fine with using a different version of Windows, as long as I can install it. Problem is, I need to make it bootable from my USB drive, which is what I am asking. Every guide I have come across needs me to do it from Windows, and as I do not have Windows (well I do, but nothing loads anyway) I need to know how I can use an iso file to make it work.

As I said before, my CD/DVD drive isn't a burner, so I can't just burn the iso to a disc.

If somebody can help me I would appreciate it.

---

