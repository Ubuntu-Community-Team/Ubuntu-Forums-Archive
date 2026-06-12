---
title: "[SOLVED] Messed up my xorg.conf and now my monitor doesnt work!"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by ToxicNostalgia on 2008-12-20
Yesterday, I decided to make the somewhat scary jump from windows to kubuntu 8.10. Everything was going great until i tried to switch my resolution by using nano to edit my xorg.conf file. I forgot to make a backup and added one line of code (I think it was Modesize "1280x1024@60") to the monitor section. After seeing no effect, I shut of my computer for the night, and this morning,  I attempted to boot up my computer, and to my horror,  my monitor ceased to work. I am sure that everything is plugged in correctly, etc. It seems that my uninformed little addition has caused this big problem. As I write this on my ipod touch, I hope that there is some sort of fix. Maybe I could somehow reinstall kubuntu or go into a mode where I could fix the error with the aid of my monitor. Perhaps, a recovery disk of some sort that could wipe my hard drive clean so I could use my monitor again? Someone please help me. It would be greatly appreciated.

---

### Post by Zeedok on 2008-12-20
Try booting your computer with a Live CD, then copy the xorg.conf from the Live CD onto your hard drive installation.  Hopefully that will sort out your problems.

---

### Post by ToxicNostalgia on 2008-12-20
I tried booting it up with the live cd, but my monitor still doesn't display anything. It won't display even the boot up screen which makes this a difficult problem to remedy. Also to add a little information: the computer with the problem is a Compaq Presario SR2013WM with a HP flatscreen monitor which measures out to be 17" and has "HP vs17x" on the bottom front corner. When I boot up my computer the monitor doesn't display anything, and its LED light just blinks over and over no matter what I do. I have turned it off and on as well as unplugging and connecting it again many times to no avail.

---

### Post by jrusso2 on 2008-12-20
If you have SSH running you can try to SSH in from another PC and either fix the error or copy another xorg file.

---

### Post by Zeedok on 2008-12-20
> When I boot up my computer the monitor doesn't display anything, and its LED light just blinks over and over no matter what I do. I have turned it off and on as well as unplugging and connecting it again many times to no avail

Even if you stuff up your xorg.conf you should still be able to boot with the liveCD (or Windows if you are still dual booting).  Does the GRUB menu come up when you reboot?  Can you select the "Last successful boot" option (or whatever it is called)?

How soon after editing your xorg.conf did you run into trouble (ie next boot or a few days later)?? ie Could you be having a hardware, rather than software issue??

---

### Post by ToxicNostalgia on 2008-12-20
I like the idea, however, I do not have SSH running, and it is difficult to know where I am because I'm literally playing in the dark. Maybe someone could tell me exactly what to press to fix the problem but that would be extremely difficult to pull off. Isn't there some kind of disk that I could pop into my computer that would take kubuntu off my computer so I could regain use of my monitor? (After which, I would be able to reinstall kubuntu and start fresh.)

EDIT: I experienced the issue on the next boot. I am not dualbooting and absolutely nothing shows up on my monitor, not even the boot screen ABSOLUTELY NOTHING at any point during the process. So it could very possibly be a harware issue, but I have never had any troubles before.

EDIT 2: In light of the above post, I have concluded that it most likely a hardware issue. If a different monitor doesn't work, I will revive this thread. Thanks to everyone who helped, I appreciate it.

---

### Post by Elfy on 2008-12-20
When you can get to see the screen boot to recovery mode, from the menu you can pick xfix - this will give you a new basic xorg. Once that's done you can edit the file again and restart x.

In future try and use the -B option with nano - it will then create a backup for you.

sudo nano -B /file/name 

It is possible if you didn't get it right that you've broken the monitor.

---

### Post by igknighted on 2008-12-20
Does the system even POST?  If you don't even see the post screen, then it can't be an Ubuntu issue.

As far as damaging the monitor with incorrect settings... this was an issue years ago.  If you got the refresh rates wrong on some CRTs they could explode.  But as far as damaging a modern LCD by asking it to hold a higher resolution, I am extremely skeptical that this could happen.  Not only is the resolution not potentially dangerous like refresh rate, but modern monitors have protections built in, just in case.

---

### Post by Zeedok on 2008-12-20
OK, so now we're starting to get out of my comfort zone.  If you don't even get GRUB loading at all (NB this should show up before the Linux kernel is loaded and way before xorg.conf is loaded) then I suspect you've somehow done something to your [master boot record]("http://en.wikipedia.org/wiki/Master_boot_record").  If I am correct (which I **can't** guarantee) the MBR is the blueprint of where the computer looks for the operating system - it contains the primary partition table.  I think I had this type of problem before (and I think I booted into windows and reformated my linux partition and re-installed, obviously not something you can do at present).

AFAIK a corrupt MBR _still_ wouldn't prevent you from booting from a live CD. I agree that without access to even the command line, it is difficult to find a solution.  You could try searching the forums for references to "MBR" or the "primary partition table" to see what else you could try.

I would also suggest re-posting your problem with a reference to "Boot error" or "GRUB won't load" - this might attract some better qualified assistance.  By all means, mention that you have just edited the xorg.conf - maybe I am incorrect about Xorg ([here's a copy of the manual]("http://linux.die.net/man/5/xorg.conf")).  Maybe we can both learn something with a little help from a power user??

---

### Post by Elfy on 2008-12-20
Personally I suspect that this is a hardware issue - but until the OP comes back following his Edit2 of post 6 no-one will know :)

I've done similar in the past to monitors :)

---

### Post by billgoldberg on 2008-12-20
If this bios screen and the grub doesn't show, it isn't a xorg problem.

It's your monitor that's busted.

---

### Post by ToxicNostalgia on 2008-12-20
For all those who said it was a hardware issue, you were right. I should have known that if absolutely nothing was showing up then it couldn't be an xorg.conf issue. I do not believe that I ruined my monitor by trying to force it to display it's recommended settings (1280x1024@60). After all, those are the settings that it always displayed at in windows. I guess it was just a freak coincidence that my monitor decided to give out after I made a harmless addition (even though it probably wasn't correct) to my xorg.conf. Luckily, my friend gave me one of his extra monitors that he no longer uses. However, my new question is why wouldn't KRandRTray just show 1280x1024 as one of the size options? I don't understand why it only gave me lame options (800x600,640x480,400x300,320x240), well under my monitors capabilities.

---

