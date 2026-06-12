---
title: "How can I find the Windows xp recycler"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Mad,professor on 2009-12-31
Hi Guys,

Some time ago I installed my Ubuntu 9.10 and I am very happy with it. I used Ubuntu and Windows xp because sometimes I needed the Dos mode of windows.

I think I have unfortunately deleted some files from my C: windows partition. When I now try to load my windows the error occurs:

NTLDR is missing 
press Ctrl + alt + del 

That was no problem for me because I stopped working on Windows. But now I have to use the Dos editor and some other windows applications again.
Is it possible to get access to the windows recycler over Linux and restore these files?
Or what can I do to fix my windows?
I do not want to reinstall it because my music and all files are still on the windows partition.

Thanks for your help

Andreas

---

### Post by ScottinSoCal on 2009-12-31
> **Mad,professor said:**
> But now I have to use the Dos editor and some other windows applications again.
Is it possible to get access to the windows recycler over Linux and restore these files?
Or what can I do to fix my windows?

It's very unlikely that your NTLoader file is in the XP trash can, because XP wouldn't allow you to delete that file while it was running, and your Ubuntu installation won't put things in the XP trashcan.

Windows also doesn't just move files to the trash, it renames them. So even if you found the trash can, and the file was in there, unless it was the only thing in there, you wouldn't know what to restore.

However, you can install a DOS emulator in Ubuntu and many Windows apps run just fine in WINE (the Linux Windows emulator). So you could install those and reinstall your Windows apps, and never have to leave Ubuntu again.

---

### Post by metalf8801 on 2009-12-31
I know this doesn't really slover your problem but have you tried installing a DOS Emulator in Ubuntu?  

to do this go to System > Administrator > Synaptic Package Manager 
then search for dos 
here are some of your options 

1. DOSEMU is a PC Emulator application that allows Linux to run a DOS
operating system in a virtual x86 machine. This allows you to run
many DOS applications.

2. DOSEMU is a PC Emulator application that allows Linux to run a DOS
operating system in a virtual x86 machine. This allows you to run
many DOS applications.

Also theres always freedoes which is its own OS 
[http://www.freedos.org/](http://www.freedos.org/)
and freedos can be installed in Virtualbox

---

### Post by Mad,professor on 2009-12-31
Thanks for the quick reply I will try this. But I am not sure if I have all programs I need. At the moment and for the next half year I am abroad and I think I didn't bring all installation DVDs.

So if you have any ideas how to fix it?

Than I have not deleted important Windows files but why do I have this problem then? That I deleted some files from the C: partition is the last I can remember I did in Windows.

---

### Post by QIII on 2009-12-31
Wine is not an emulator  (WINE is a recursive acronym for Wine Is Not an Emulator).  I've never used it, so I cannot speak to its usefulness for your needs.

If you have really ruined your XP installation (which I cannot say for sure.  I doubt it.  Someone may be able to help you get it running again, so hang on...) and you still have your installation disk, you can use a virtual machine like VirtualBox to install XP in.

I don't think that the free version of VirtualBox supports USB, however.  I may be mistaken.

A less attractive thing you could do is reinstall XP, but that would mean you'd have to reinstall GRUB as well since the reinstallation of XP would destroy it.

---

### Post by alzie on 2009-12-31
I've had the same issue.  The XP bootloader has become corrupted.

The fix for NTLDR is going to overwrite your Grub so you'll have to fix that after the NTLDR repair.
```

Boot XP CD (any key to boot from CD)

Press R to repair Windows

Login by pressing 1 <enter>

You should get a prompt for your administrator password here.

You'll need to copy 2 files to the root directory of your primary HD (which is probably C: )
[CODE]copy g:\i386\ntldr c:\
copy g:\i386\ntdetect.com c:\
```
Remove CD and reboot[/CODE]
You should now be booting into XP with no Grub.

To reinstall Grub I have found the directions here: [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)
which should get you back up and running.

I strongly recommend backing up your important files first. (been there done that)

I hope this helps.

---

### Post by ScottinSoCal on 2009-12-31
> **QIII said:**
> Wine is not an emulator  (WINE is a recursive acronym for Wine Is Not an Emulator).

Yeah, I know that's what it stands for, but if it walks like an emulator, and it quacks like an emulator, I'm gonna call it an emulator....

---

### Post by Mad,professor on 2009-12-31
Hey you are so fast in this forum. Unbelivable.

If that is the only way to fix it I have no chance because I have my windows Cd's left at home. What a pity.

---

### Post by Mad,professor on 2009-12-31
Or do you think I can copy the files
ndetect.com 
ntdlr
in C:
and reinstall grub then again?

---

### Post by QIII on 2009-12-31
WINE doesn't run a virtual machine and emulate machine instructions, which is what an emulator is.
 
 Not trying to be anally technical, so this is not a flame...  No harm intended.  Just an observation.

For the OP:  It is likely that the files you have are corrupt or simply missing.  I didn't find anything on a quick google, but those files may be available somewhere on the web.  Just be sure you are not violating any proprietary or intellectual property rights owned by Microsoft.  That is not appropriate, since it is ... well ... illegal.  You would also be taking the chance that a hacker with malicious intent would feed you something to turn your computer into a zombie porn server.

---

### Post by Mad,professor on 2009-12-31
Hi I can find the two files in my preload directory but they are not in the root directory C: ???

---

### Post by louieb on 2009-12-31
> I can find the two files in my preload directory but they are not in the root directory C:  You cant try coping then to c:\ 

Have a look [How to fix XP when the boot files are missing - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=813628")

---

### Post by Mad,professor on 2009-12-31
Happy new year and thanks guys,

I think the problem is solved. I copied the files in my root directory and windows is running now. I get a error message when I choose Windows in the grub menu but it starts and works good. 
Tomorrow morning I am gonna try this link:

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

 I think it will be very useful.

Thanks again
:P

---

