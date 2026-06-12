---
title: "Trouble with instable operative system"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by 2blue on 2009-06-10
I have the latest version of Ubuntu 9.04. and lots of issues going on. There is probably nothing wrong with the operative system, but I am still not an expert at this. 

I have recently reinstalled OS yet again. The problem occurs when I try to be clever and install VLC player and all the plugins that go with things among other stuff. Except for plugins I use Synaptic Package Manager for new software as that is suppose to be safest. I really would like VLC player, as many DVD's will not play with Movie Player. It might still be some way around the problem with Movie Player too, but VLC works with out any fuzz!!!! I would also like to add Opera, but that is like asking for trouble. 

The thing now is that I don't dear add any new software, because every time I do I get trouble. Things get utstable, mouse-pad locks, fire fox act up, pidgin suddenly cannot login to my email accout (I don't dare activate Evolution).   

After a period of hang-ups, Ubuntu performs a system check when booting. I know it sooner or later finds a flaw that prevents it from booting. I am ask to perform a four letter command (fsck or something like that, sorry I didn't write it down.) Luckily I have managed to retrieve important documents with Puppy Linux (run as a live CD from RAM) before I have been forced to reinstall OS. 

Have you experts any thoughts on this? Is there some safe or right way to install software? Is it a nown problem? 

I would be very grateful for any help :-)

---

### Post by t0p on 2009-06-10
> **2blue said:**
>    
After a period of hang-ups, Ubuntu performs a system check when booting. I know it sooner or later finds a flaw that prevents it from booting. I am ask to perform a four letter command (fsck or something like that, sorry I didn't write it down.) Luckily I have managed to retrieve important documents with Puppy Linux (run as a live CD from RAM) before I have been forced to reinstall OS. 

Have you experts any thoughts on this? Is there some safe or right way to install software? Is it a nown problem? 


Installing software through Synaptic is the safest way of getting new apps.  Your problems sound most confusing.  All I can suggest is, when the system asks you to perform the "four letter command", you do it.  Alternatively, remember to write the command down so someone here can advise you further.

I really don't know what else to say.  There is no "better" way to install software than Synaptic or apt-get (the command line version of Synaptic - basically the same thing).

---

### Post by lisati on 2009-06-10
Using "Add/Remove" on the Applications menu is sometimes easier, and is just as safe as using synaptic.

Have you had a look [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")?

---

### Post by sandyd on 2009-06-10
> **2blue said:**
> I have the latest version of Ubuntu 9.04. and lots of issues going on. There is probably nothing wrong with the operative system, but I am still not an expert at this. 

I have recently reinstalled OS yet again. The problem occurs when I try to be clever and install VLC player and all the plugins that go with things among other stuff. Except for plugins I use Synaptic Package Manager for new software as that is suppose to be safest. I really would like VLC player, as many DVD's will not play with Movie Player. It might still be some way around the problem with Movie Player too, but VLC works with out any fuzz!!!! I would also like to add Opera, but that is like asking for trouble. 

The thing now is that I don't dear add any new software, because every time I do I get trouble. Things get utstable, mouse-pad locks, fire fox act up, pidgin suddenly cannot login to my email accout (I don't dare activate Evolution).   

After a period of hang-ups, Ubuntu performs a system check when booting. I know it sooner or later finds a flaw that prevents it from booting. I am ask to perform a four letter command (fsck or something like that, sorry I didn't write it down.) Luckily I have managed to retrieve important documents with Puppy Linux (run as a live CD from RAM) before I have been forced to reinstall OS. 

Have you experts any thoughts on this? Is there some safe or right way to install software? Is it a nown problem? 

I would be very grateful for any help :-)

seems like hard disk problem to me.

---

### Post by 2blue on 2009-06-11
I let a sofware program check my harddrive and it came out ok, but that was just after a newly installed Ubuntu. 

If I don't add new programs that might conflict with all ready installed programs like Movie Player and VLC player, two browsers like Fire Fox and Opera, everything runs fine. 

Anything else I could try?

---

### Post by nandemonai on 2009-06-11
Your problem isn't conflicts that's for sure. All those packages work fine with each other.

I'm wondering if you've hit the 'Jaunty freezes for no apparent reason' bug(s).

What hardware are you running and what file system? Would it be ext4 by chance? Intel graphics?

Either that or as mentioned previously it may be hardware failing.

---

### Post by 2blue on 2009-06-11
I down loaded some kind of streamer plugin for Fire Fox from Youtube, and then the hang-ups began. I am convinced this is the reason for the trouble. I ran yet again the haddisk drive check, but still ok.

---

### Post by Bearly Able on 2009-06-11
I had the same problem, only I kept attributing it to the Nvidia driver.  Once I'd ruled that out as a cause, I had to look elsewhere, and eventually found the "Jaunty freezes for no apparent reason" bugs.  It took me a while to even bother reading these, as the bug supposedly only affects 64-bit systems, and I was running 32-bit.  However, I ran across [this thread]("http://ubuntuforums.org/showthread.php?p=7305952#post7305952"), which referred to exactly my problem.  It's listed as a bug on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691"), although again it says it affects 64-bit systems.

Eventually, my install became so unstable I couldn't boot at all and resorted to a fresh install of Intrepid.  Upgrading the kernel is suppposed to fix the problem for 64-bit.  

I was running 32-bit Jaunty with ext3 and Nvidia graphics card.

---

