---
title: "Duel Boot Question...and then some :)"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Nomad68 on 2009-03-19
I just installed Ubuntu on my old Dell to try it out and it seems pretty nice so I think I may want to install the 64 bit version on my newer PC and Dual Boot. I'm also thinking about adding another hard drive to my computer just for Ubuntu. Some questions I have are...

1, Is adding another hard drive just for Ubuntu possible? If I did that would it all run there and not interfere with my Vista stuff?

2, If I dual boot and its on another hard drive will it still pop up at computer boot up and ask me which OS I want to boot into or can I set it to boot into one all the time unless I change it?

3, Does Linux need virus protection? I've never heard of it but that doesn't mean anything lol I'm so new I am sure I'd miss it. 

4, I'd just like to ask that if I try this can some pros here please offer their tips and tricks? I'd really appreciate it. 

Thanks everyone this place is awesome. 

Steve

---

### Post by gRnt on 2009-03-19
Hi mate I have just finished going through this process myself (except I boot into XP) I've been using Linux for about a week but it is simple enough.

Yes you can install Ubuntu on a seperate Hard drive, or in a seperate partition, whichever is easier. I just did a guided install on a full hard drive, rebooted using the live CD and then used Gparted (its in the administration tab) to make some other paritions for my media (an ntfs drive so both operating systems can access it) and then an ntfs partiton for my XP install. That way I can format both OS's with touching my media.

Dual booting is simple enough, I recommend installing Ubuntu first then using the following guide [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

It's a fairly simple process, I don't even boot into Windows save using itunes for my ipod touch 2g as I'm not really happy with the work arounds so far but that is hardly the linux communities fault and rather Apples.

Good luck its very rewarding once you get a good dual boot set up well!

---

### Post by Nomad68 on 2009-03-19
Thanks for the reply man I appreciate it. I already have vista on there so I want to install Ubuntu next. 

Thanks again.

---

### Post by Nomad68 on 2009-03-19
Anyone else? :D

---

### Post by Paqman on 2009-03-19
> **Nomad68 said:**
> 
1, Is adding another hard drive just for Ubuntu possible? If I did that would it all run there and not interfere with my Vista stuff?


Definitely possible, but if you've got the space it'd be a lot cheaper to just partition off some space on your existing drive.

> 
2, If I dual boot and its on another hard drive will it still pop up at computer boot up and ask me which OS I want to boot into or can I set it to boot into one all the time unless I change it?


You can set any OS to be the default. A good GUI for managing this (and many other things) is startupmanager.

> 
3, Does Linux need virus protection? I've never heard of it but that doesn't mean anything lol I'm so new I am sure I'd miss it. 


Nope. As long as you're patched up to date and don't go installing dodgy software (ie: stick to the repos) then you don't need to worry.

> 
4, I'd just like to ask that if I try this can some pros here please offer their tips and tricks? I'd really appreciate it. 


You might want to consider mounting /home on a separate partition. It makes reinstalling really easy, which is nice if you break your system in a moment of noobishness (don't worry about that, we've all done it ;) )
Also, some good packages:
ubuntu-restricted-extras: installs all your multimedia codecs, Flash, Java, MS fonts, etc in one go
startupmanager: mentioned above, very handy
ntfs-config: sets up mounting your NTFS partition
sbackup: automate your backups
compizconfig-settings-manager: tweak your compiz effects

Also, the Medibuntu repository is worth having. Includes DVD playback, Skype, etc.

---

### Post by Nomad68 on 2009-03-19
Man thanks a lot for the info very helpful. I been watching a LOT of youtube I know about medibuntu lol. 

I'll let you know what happens if I do it. Already put it on old Dell I like it.

---

