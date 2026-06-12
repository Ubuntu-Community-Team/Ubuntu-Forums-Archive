---
title: "Grub grumbles"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Ronve3 on 2009-11-10
Permit me a small rant about the grub boot loader.  Grub, in my opinion, has probably turned more people off  Linux than any other single factor.  It’s a piece of software designed by geeks, for geeks, and only to be maintained by geeks.  

What led to all this? I’ve just spent the better part of two days trying to install a Wubi version of Ubuntu.  The first install appeared to go okay and when I rebooted I got the grub screen with two choices of operating systems, WordPerfect XP and Ubuntu.  The only problem was Ubuntu didn’t work.  Instead I was presented with a grub shell prompt, and although “help” presented an assortment of choices, none of them worked – or even presented a clue as to how they might work.

So I uninstalled Ubuntu using the Windows control panel facility. Even though the Ubuntu uninstaller flashes a brief message saying that it is removing the boot loader, it lies.  Grub is still there.  And still unusable.

Well, I thought, maybe my download file was corrupted. I did another download and this time I made sure to check the mdsum to make sure it was complete. (Later, I went back and checked the checksum on the original file – it was identical.)

At this time I was relying on a new installation to rewrite the original grub code, thus getting rid of any problems. Faint hope.  Grub was still there and still presenting the shell prompt.

Along the way, I made the mistake of trying another installation on my laptop computer – with exactly the same results.

I turned to the Internet and googled for some way to get rid of grub.  Several users suggested going to the repair console after booting from the XP CD, and using the fix boot and fixmbr commands. I did both, and it made not the slightest difference.  Grub still survives.

I’ve read  everything I can find on changing or deleting grub, but most of it assumes one is already in Linux – and of course my problem is that I can’t even get to Linux.

I’ve been playing around with microcomputers for 30 years now, and I’ve made several previous attempts to run Linux, always on a separate partition.  I greatly admire the operating system.  But problems with grub led me to give up on at least one previous installation, and I would never have tried wubi if I had known in advance that it used the grub boot loader.

So I’m open to suggestions for some viable method of cleaning grub off my hard disk.  In the meantime I’ll continue to assume that grub is the greatest obstacle to acceptance of Linux.

And I remain grateful that my windows XP installation survives, praise be to Bill Gates.

– Ron

---

### Post by necromonger on 2009-11-10
use your xp cd go to cnd prompt type in bootrec.exe/fixboot and then type bootrec.exe/fixmbr and that should do it.

---

### Post by Ji Ruo on 2009-11-10
What version of Ubuntu did you try to install with WUBI - was it the latest version (9.10 Karmic Koala)?

The latest version uses GRUB2 which is very new. Actually it's so new it's not even GRUB2 yet - it's GRUB 1.97Beta4. It's probably making a bad situation worse, because really it's not ready for release yet.

GRUB (and by this I mean GRUB1, the original) is pretty ugly stuff for the end user, but when you compare it to the alternatives it's streets ahead. If you use GRUB in a comparable way to the Windows bootloader ie. one OS on one system, you would have an identical experience and not even be aware of its existence beyond a brief startup message. It's only because GRUB gives so much more control over your computer that people are aware of the problems of dealing with it, as they dual- or multi-boot operating systems etc.

If you still want to try out installing with WUBI you could ask for specific help on what's going on. The previous version of Ubuntu (9.04 Jaunty Jackalope) will likely be less problematic than the latest release.

---

### Post by Ronve3 on 2009-11-10
> **necromonger said:**
> use your xp cd go to cnd prompt type in bootrec.exe/fixboot and then type bootrec.exe/fixmbr and that should do it.

Correct me if I'm wrong, but my impression is that bootrec.exe is for use only with Vista and windows 7.  Both my systems use windows XP, and the windows XP repair console already has fixboot and fixmbr available.  As I said in my original message, I've already tried both, without success.

Thanks anyway.

-- Ron

---

### Post by necromonger on 2009-11-10
did you try it?

---

### Post by Ronve3 on 2009-11-10
> **Ji Ruo said:**
> 
The latest version uses GRUB2 which is very new. Actually it's so new it's not even GRUB2 yet - it's GRUB 1.97Beta4. It's probably making a bad situation worse, because really it's not ready for release yet.

Yes, the one that's been giving me so many problems is indeed grub 1.97 beta 4.

So do you think a wubi installation of Ubuntu 9.04 might clear my grub problems?  I'm getting a little gun shy.

-- Ron

---

### Post by Ronve3 on 2009-11-10
> **necromonger said:**
> did you try it?

I have now.  Didn't work. 

My XP Home SP2 disk doesn't recognize bootrec.exe as a command, followed by either /fixboot or /fixmbr.  

-- Ron

---

### Post by falconindy on 2009-11-10
The commands are fixboot and fixmbr. They're not flags for some other command.

Editorial: I stopped reading your post when you said Grub is "for geeks, by geeks, etc". Apparently, The Windows bootloader is so much easier because you've clearly had great success restoring it. Any bootloader, by design, must be an extremely simple and universally supported piece of software. Because of that, it can sometimes seem a little unfriendly to a user. However, try doing **anything** that Grub does on a daily basis with the Windows bootloader and I think you'll find that Grub isn't really so bad.

---

### Post by Desert Sailor on 2009-11-10
> **Ji Ruo said:**
>  ...The latest version uses GRUB2 which is very new. Actually it's so new it's not even GRUB2 yet - it's GRUB 1.97Beta4. It's probably making a bad situation worse, because really it's not ready for release yet. 

I am really not wanting to start some kind of flame war here, but if Grub wasn't ready for release, Why was it released?  Wouldn't it have made much more sense to hold off until 10.4 or even 10.10 and release to the community a stable, working product which can be understood and supported? 

Combining Grub2 errors and Network Manager errors, it seems like 9.10 was just thrown up on the servers while still in beta testing....

---

### Post by louieb on 2009-11-10
> **Ronve3 said:**
> ...when I rebooted I got the grub screen with two choices of operating systems, WordPerfect XP and Ubuntu.  The only problem was Ubuntu didn’t work....
So I uninstalled Ubuntu using the Windows control panel facility. Even though the Ubuntu uninstaller flashes a brief message saying that it is removing the boot loader, it lies.  Grub is still there.  And still unusable.

With a Wubi install the 1st boot loader you see is the the Windows boot loader. In XP its called ntldr and it get its information from file **c:\boot.ini **

Ubuntu and GRUB are gone after running the windows Ubuntu uninstaller. However the uninstaller does not always cleanup boot.ini.  

You can use notepad to remove the Ubuntu entry. 
> bootrec.exe is for use only with Vista and windows 7. Both my systems use windows XP, and the windows XP repair console already has fixboot and fixmbr available.You are correct.  

Just a side note: a WUBI install does nothing that would require ever running fixboot or fixmbr. 
> So do you think a wubi installation of Ubuntu 9.04 might clear my grub problems?  I'm getting a little gun shy.

I'm not a fan of WUBI installs - its the easiest way to install Linux - when it works.  Its also the hardest to fix when it breaks.

If you have a couple of gig of ram or more:  I would use [VirtualBox]("http://www.virtualbox.org/")  and install Ubuntu in it.  

Jaunty (v9.04) or Karmic (v9.10) ...  I dual boot both on my laptop. Still use Jaunty more - just like it better. Karmic does have some programs not available in Jaunty.

---

### Post by Ronve3 on 2009-11-10
> **louieb said:**
> With a Wubi install the 1st boot loader you see is the the Windows boot loader. In XP its called ntldr and it get its information from file **c:\boot.ini **

Ubuntu and GRUB are gone after running the windows Ubuntu uninstaller. However the uninstaller does not always cleanup boot.ini.  

You can use notepad to remove the Ubuntu entry. 

I can see the Ubuntu reference in Notepad and delete the line, but I'm not allowed to write the edited file (apparently because it's read-only).  I'll have to do some reading to find out how to get around that obstacle.   


> **louieb said:**
> If you have a couple of gig of ram or more:  I would use [VirtualBox]("http://www.virtualbox.org/")  and install Ubuntu in it.  

No, I don't have much memory.  My old desktop pentium 3 motherboard is maxed out at 512 mb. The laptop has 1 gigabyte (it's supposed to handle 1.5 gb, but i've never found any combination of memory that would work in it at the 1.5 gb level).  It's a slow Celeron processor anyway (1.5 ghz) -- too slow for VirtualBox.  As  you may have gathered from my earlier typos (Wordperfect XP instead of Windows XP) and general air of exasperation, I'm also quite old and willing to give up on Linux for the moment.  But I would like to restore both my computers to their former state.  

incidentally, I did find a CD with Ubuntu 9.04 that I had downloaded some months ago, and tried doing a wubi install with that.  The results were similar in that when I tried to enter Ubuntu I wound up at the grub shell prompt again.  It was a different grub prompt and evidently from a much earlier version of grub, but the net effect was the same.  Either there is some rogue code left over from my earlier attempts or there's just something about my system that grub doesn't like.

Thanks for your help and your comments about fixmbr, fixboot and bootrec.exe.

-- Ron

---

### Post by Ronve3 on 2009-11-11
> **louieb said:**
> 

You can use notepad to remove the Ubuntu entry. 


Just to finish this thread, I did succeed in removing the Ubuntu line from boot.ini (by the somewhat circuitous route Microsoft suggests, found by googling for "how to edit boot.ini in Windows XP") and all is well, and back to normal in my Windows bootup.  

I wonder if *anyone* has succeeded in a Wubi install of 9.10?  Or, to put it another way, am I the only one that had difficulty?

-- Ron

---

### Post by louieb on 2009-11-11
Best thing to do is try a distributions Live CD. The OS runs from the CD and does not change anything on the computer.   [DistroWatch.com Use Linux, BSD]("http://distrowatch.com/") 

Funny thing about Linux distributions.  On a given computer some will install and everything works without any problem.  Some just won't install or if they do the display is weird or sound does not work.  

Sometimes its hardware. I have an Acer 19 wide screen display. It does not reports itself correctly, when I 1st installed Ubuntu  I had to manually configure xorg in order to get the 1440x900 native resolution.  

When I tried Puppy Linux on the same computer - same Acer display - Puppy picked it right up and was able to select  1440x900 resolution without any manual configuration at all.  In fact I used the Puppy xorg.conf to fix the resolution in Ubuntu. 

> 
incidentally, I did find a CD with Ubuntu 9.04 that I had downloaded some months ago, and tried doing a wubi install with that. The results were similar in that when I tried to enter Ubuntu I wound up at the grub shell prompt again. It was a different grub prompt and evidently from a much earlier version of grub,


v9.04 uses GRUB legacy.  I haven't seen it change since I started using Linux in 2005. Really kind of surprised that your having the same kind of problem. 

Ubuntu Karmic is the 1st of popular Linux distributions to use GRUB2 as its boot loader by default. It has new features and it seem a few bugs that still need to be worked out.   Just a guess that Fedora, Open Suse and others will soon use it too.

---

