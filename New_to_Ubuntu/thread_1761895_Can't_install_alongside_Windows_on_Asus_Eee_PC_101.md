---
title: "Can't install alongside Windows on Asus Eee PC 1015PED"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-05-18
Just acquired an Asus Eee PC 1015PED with Windows Seven Starter OS.

I put Ubuntu 11.04 on a USB drive, tried it & then attempted to install it from the Ubuntu desktop.
Unlike the instructions, there was no option to install Ubuntu alongside W7, only INSIDE (or instead or manual).

Is this because there are already too many primary partitions or what?
Disc Manager shows:
C: 100G Primary
D: 117G Primary
No name: 15G Primary (could this be recovery?)
No name: 20M EFI System Partition

Computer shows:
C: 100G
D: 117G
Q: 0G (MS Office click-to-run 2010)

Is the option to install INSIDE Windows the same as I see called Wubi?
How inferior is that to the real thing?

Thanks for all comments!

---

### Post by mike555 on 2011-05-18
Yes you are only allowed 4 primary partitions , you can use gparted from the live cd , to delete one (be careful and make sure it's big enough ) then format it as an  extended partition , then install Ubuntu to it ........
 you might want to read more about this first.

---

### Post by wildmanne39 on 2011-05-18
> **2CV67 said:**
> Just acquired an Asus Eee PC 1015PED with Windows Seven Starter OS.

I put Ubuntu 11.04 on a USB drive, tried it & then attempted to install it from the Ubuntu desktop.
Unlike the instructions, there was no option to install Ubuntu alongside W7, only INSIDE (or instead or manual).

Is this because there are already too many primary partitions or what?
Disc Manager shows:
C: 100G Primary
D: 117G Primary
No name: 15G Primary (could this be recovery?)
No name: 20M EFI System Partition

Computer shows:
C: 100G
D: 117G
Q: 0G (MS Office click-to-run 2010)

Is the option to install INSIDE Windows the same as I see called Wubi?
How inferior is that to the real thing?

Thanks for all comments!
Hi, this should help. [http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

### Post by Rex Bouwense on 2011-05-18
Yes, a Wubi install is inside of Microsoft Windows.  Ubuntu would then be considered just another Microsoft program and could be uninstalled from the add/delete program.  Wubi will give you an idea of the Operating System but is not really meant as permanent thing.

---

### Post by 2CV67 on 2011-05-19
Thanks for your replies!
> **Rex Bouwense said:**
> Wubi will give you an idea of the Operating System...

Well, my first impression is not good! (By the way, I have been multi-booting Ubuntu on my old desktop since Edgy - see signature).

On my wife's brand-new netbook, which I don't want to hack about too much yet & which will not allow installing Ubuntu without seriously modifying existing partitions, I tried the "easy" way using Wubi.

The first time I tried to shut down, the button had no shutdown option in the menu & nothing else seemed possible, so I had to do a hard shutdown on the switch.

The second time, there was a shutdown option & I could confirm it OK, but then froze at a screen with wallpaper & nothing else.
No mouse pointer & no keyboard actions (Esc - Ctrl/Alt/Del - REISUB etc).
So another hard shutdown.

I just tried a third time & that was exactly the same as the second.

Altogether not encouraging!

Edit: I will start a new thread for the Wubi question(s)...

---

### Post by 2CV67 on 2011-05-20
Well, having read as much as I could find on this, like:
   [https://bbs.archlinux.org/viewtopic.php?id=103974](https://bbs.archlinux.org/viewtopic.php?id=103974)
then I have decided it is too risky to try putting Ubuntu alongside Windows on this particular netbook, unless I can find clear & simple instructions from somebody who has successfully done exactly that.
I would have prefered to find good instructions on the Ubuntu download page...
Pity!

As the Wubi option is also limping badly:
   [http://ubuntuforums.org/showthread.php?t=1763308](http://ubuntuforums.org/showthread.php?t=1763308)
then it looks like I may be leaving Ubuntu altogether.
Pity!
:( :(

Actually, Windows Seven is not bad.
And, of course, works out of the box...

---

