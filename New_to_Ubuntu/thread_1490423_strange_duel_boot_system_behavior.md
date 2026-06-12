---
title: "strange duel boot system behavior"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by pdlethbridge on 2010-05-22
I have arranged my computer to be a duel boot system.  9.04 using 15 gigs with a 20 gig home file and 10.04 using 15 gigs with a 15 gig home file. There is also a 2 gig swap file and a 12 gig fat 32 partition on a 80 gig hard drive.
   I have noticed a couple of things that I have questions about. 
9.04 is the first OS on the drive but it shows up second in grub. Is there a way to make it the default boot system?
   I had added pictures to my desk top last night in 9.04 but they are not there this morning.
I normally turn off the sound when I shut down to avoid the start up sounds,again in 9.04, but the were heard this morning.
Is there a conflict between the two home folders? Or is something else going on?
Thanks in advance, Paul

---

### Post by pdlethbridge on 2010-05-22
Let me throw this into the mix. Both OS's use the same name and pass word, could this cause the conflict?

---

### Post by goldshirt9 on 2010-05-22
well i'm unsure of the grub priority .
although i know from experience that the last system to be installed becomes the 
default system for me.

is your desktop picture on the partition hdd so both o/systems can read it.

if so then i believe you have to mount the hdd so the o/system can get access .
and so restore the picture.

i had a similare problem and then realised the picture had to be on the o/system at boot up 
for it to automatically be used.
ref the sound i'd say it was just a glitch.
i dont use a password for my login but after a update i have to input the password again to log in . 
this doesn't always happen but i can live with it.

---

### Post by warfacegod on 2010-05-22
The best way I have found to get rid of the sounds is to remove ubuntu-sounds from Synaptic.

```
sudo apt-get install startupmanager
```

Will help with your GRUB order. You should install it in the first one in the list because that is the OS that is "controlling" GRUB. You can use it to change the default OS among other things.

Identical username and password shouldn't be causing you any problems like you describe. I do the same thing. If you had the two sharing a /home partition or folder that might be a different story.

---

### Post by cgroza on 2010-05-22
Yes, it can...

---

### Post by pdlethbridge on 2010-05-22
That's what I like to see, 100% confusion. They both have their own home folder.It's arranged like so:
9.04 OS
9.04 home
10.04 OS
10.04 home.
swap
fat 32

---

### Post by warfacegod on 2010-05-22
> **cgroza said:**
> Yes, it can...

Care to elaborate?

---

### Post by QLee on 2010-05-22
[QUOTE=pdlethbridge]That's what I like to see, 100% confusion. [/QUOTE]

Yes. you do seem confused. Probably that is why you don't check the wiki or use forum search to look for the answer to any of your questions.

   [QUOTE=pdlethbridge]I have noticed a couple of things that I have questions about. 
9.04 is the first OS on the drive but it shows up second in grub. Is there a way to make it the default boot system?[/QUOTE]

Yes, either change the default OS in GRUB ( in /etc/default/grub) or make a custom menu.

You might find one of these helpful:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=1296225](http://ubuntuforums.org/showthread.php?t=1296225)
Edit: This one is not Ubuntu specific but might help
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html) (end edit)


[QUOTE=pdlethbridge]Is there a conflict between the two home folders? Or is something else going on?[/QUOTE]

Probably something else as you only have them mounted in the correct OS, eh? ...Or, is that not the case?

Keep in mind that you had legacy GRUB with 9.04 and GRUB-PC (GRUB2) with 10.04, and Lucid was installed last so it put itself first on the menu. Now that you are using GRUB2 don't try to update legacy GRUB when you are booted into 9.04.

I have no clue about what might have happened to your pictures.

---

### Post by pdlethbridge on 2010-05-22
In fact I do check the wiki's and forum search as I've been able to solve problems I've had with ubuntu for 4 years since I quit Windoze. Sometimes it's been hard to find the right answer for my problems. 
The easiest thing I could do is stick with 9.04 and never try something new. I like the looks of 10.04 but, like 9.10, it has been a bit buggy with my computer. I won't stop trying to fix things. Maybe I don't ask the right questions or I should do more by myself, but that may make or break my use of Ubuntu.

---

### Post by warfacegod on 2010-05-22
> Yes. you do seem confused. Probably that is why you don't check the wiki or use forum search to look for the answer to any of your questions.

That seems a bit uncalled for.

---

### Post by QLee on 2010-05-22
[QUOTE=pdlethbridge]That's what I like to see, 100% confusion. ...[/QUOTE]

That's what I was responding to, and with the correct answer too.

---

### Post by lisati on 2010-05-22
I'll leave the comments about the two installations duelling aside for now.... :)

---

### Post by QLee on 2010-05-22
[QUOTE=lisati]I'll leave the comments about the two installations duelling aside for now.... :)[/QUOTE]

Well, they won't "duel" if the OP follows my advice on not letting the legacy GRUB system (9.04) do a GRUB update and only let GRUB2 discover and update grub. I hope he understood that from what I wrote.

---

### Post by warfacegod on 2010-05-22
I've seen the "duel" mistake many times in the forums. Besides, anybody that's tried to get Windows to dual boot, especially with another Windows, knows that duel is the correct term.

---

### Post by QLee on 2010-05-22
[QUOTE=pdlethbridge]In fact I do check the wiki's and forum search as I've been able to solve problems I've had with ubuntu for 4 years since I quit Windoze. Sometimes it's been hard to find the right answer for my problems.[/QUOTE]

Yes, that is why I agreed with you about confusion. Also why I did the search and gave you the links.


[QUOTE=pdlethbridge]The easiest thing I could do is stick with 9.04 and never try something new. I like the looks of 10.04 but, like 9.10, it has been a bit buggy with my computer. I won't stop trying to fix things. Maybe I don't ask the right questions or I should do more by myself, but that may make or break my use of Ubuntu.[/QUOTE]

Well, I have no opinion on your use of Ubuntu, the choice is yours.

I did give you what I thought were the tools to get started on the issue you described and was waiting here to see if you had questions about those links or what was discussed on them. Anyone else here will try to help with questions too and people will try to help you learn some of the new concepts you need for the future.

---

### Post by pdlethbridge on 2010-05-22
I did this:
\pdleth@pdleth-desktop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-18-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
But there is no reference to 10.04

---

### Post by warfacegod on 2010-05-22
I'm not certain about this but I don't think GRUB can boot 10.04. You'll need GRUB2.

Section 13 will walk you through installing GRUB2: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

Then do:

```
sudo update-grub
```

again.

---

### Post by pdlethbridge on 2010-05-22
From the looks of things around here, I'm not the only one having problems. This is not ready for prim time. Guys, if you want people to use the OS, make it easier to run.PLEASE!
I made it easier for me, I got rid of 10.04 and ONLY have 9.04 on my computer, All problems solved!. end of problem!

---

