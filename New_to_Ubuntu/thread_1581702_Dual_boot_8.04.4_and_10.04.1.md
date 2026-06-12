---
title: "Dual boot 8.04.4 and 10.04.1 ?"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by Stunt Double on 2010-09-25
Is it possible to install 10.04.1 on a system that already has 8.04.4 installed? 
NOT an upgrade. 
I want to be able to choose between them at start-up. 
Or will there be a conflict between Grub and Grub 2?
Thanks

---

### Post by sudeepk on 2010-09-25
Yes you can install 10.04 without effecting the previous version. During the installation select a different partion. I don't think there would be any conflict between the grubs.

---

### Post by JKyleOKC on 2010-09-25
Only one of the two grub versions can be installed in the MBR, but it's my understanding that if Legacy Grub is already in place, then the Lucid installation will use it instead of Grub 2. I know that was the case for the first revision that came out using Grub 2 but do not know whether it's true for a new install as opposed to an upgrade...

---

### Post by Rubi1200 on 2010-09-25
If you create a separate partition for 10.04 there is no reason for it not to work.

But, you will then have to decide whether you want to use GRUB2, which 10.04 would install by default, or continue using legacy-GRUB, which 8.04 uses.

If there is an option in the installer of 10.04 not to install a bootloader you could do it like that and then run ```
sudo update-grub
``` in 8.04 afterwards or reinstall legacy-GRUB from the 8.04 CD after installing 10.04 (assuming you let it install the GRUB2 bootloader).

On the other hand, GRUB2 can happily pick up 8.04 and add an entry to the GRUB menu.

Either way, if you have more questions feel free to ask.

---

### Post by sikander3786 on 2010-09-25
Rubi has explained nearly everything. I just want to say if I was doing this, I would just free up space for Lucid, create a new partition and install Lucid. Let GRUB2 install and pick it my existing installation for dual boot.Thats it. The easiest way.

---

### Post by Rubi1200 on 2010-09-25
> **sikander3786 said:**
> Rubi has explained nearly everything. I just want to say if I was doing this, I would just free up space for Lucid, create a new partition and install Lucid. Let GRUB2 install and pick it my existing installation for dual boot.Thats it. The easiest way.
+1

Some people, however, feel more comfortable with the older version of GRUB and wish to retain it even though GRUB2 is the way of the future (for now).

And, just to be clear, legacy-GRUB was only retained when upgrading to 9.10 if the user decided to keep that option. A fresh install will always load GRUB2 unless one chooses to not install the bootloader in the advanced install options.

---

### Post by Stunt Double on 2010-09-26
I installed 10.04.1 on a separate partition and now I can't boot. Instead of the usual Grub screen, I get a screen that says:
      GNU GRUB version 1.98-1ubuntu7
Minimal BASH-like editing is supported. For the first word,TAB lists possible command completions. Anywhere else TAB lists possible device or
file completions.
grub>_
If I press TAB, I get a long list of commands.
How do I restore a working GRUB or restore my system to what it was before?
Thanks

---

### Post by sikander3786 on 2010-09-26
Boot using a live cd and post the output of bootscript from Rubi's signature following the instruction on the same page. After you've pasted selected all the text and click # code tags from the top to give it proper formatting. From that, we'll have a better idea of your partitioning and Grub setup.

Bootscript courtesy of meierfra.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Stunt Double on 2010-09-26
Problem solved! 
The 7-part script from Cariboo907 in response to this thread: [http://ubuntuforums.org/showthread.php?t=1562464&highlight=GNU+GRUB+version+1.98-1ubuntu7](http://ubuntuforums.org/showthread.php?t=1562464&highlight=GNU+GRUB+version+1.98-1ubuntu7), did the trick.
Thanks to everyone for the help.

---

