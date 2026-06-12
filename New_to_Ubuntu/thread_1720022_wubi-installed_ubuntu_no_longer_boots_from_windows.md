---
title: "wubi-installed ubuntu no longer boots from windows boot loader"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by AeoliX on 2011-04-02
I installed Ubuntu 10.04 (I think - can't access it at the moment to be able to check this out) several months ago on my laptop via Wubi.  This is the first time I had ever tried using Ubuntu.  What used to happen (and happened successfully for several months) is when I'd boot my computer the Windows Boot Loader would pop up and ask if I wanted Ubuntu or Windows XP.  I had set Ubuntu as the default, so after 30 seconds, or when I selected Ubuntu, some writing would flash up on the screen then a separate menu wold appear asking which version of Ubuntu I wanted - I always just hit enter to select the first one - which again, I can't tell you what it was because it's no longer functioning - then it booted into Ubuntu.

I had been using XP for a while because of a project I was working on, and when I went to boot back into Ubuntu, I selected Ubuntu from the Windows Boot Loader, then instead of the second menu popping up the screen flashed a bit gray, and a second later the computer rebooted.

I attempted to solve this problem myself, and being a totally Ubuntu noobie tried my best to find advice that sounded likely to work.  I now know I chose improperly, but I ended up using the Live CD to boot into Ubuntu, then did this (the syntax may not be totally correct - can't find the webpage I found this on):

sudo -i
mount /dev/sda2 /mnt
grub-install --root_directory =/mnt/ /dev/sda

After this, when I booted my computer it just booted to grub, and not the Windows Boot Loader.  This was unfortunate, since I didn't actually have a Linux partition since I usd WUBI, so I couldn't figure out how to get grub to boot to Ubuntu.

So then I used my WInXP recovery disk to repair the Windows Boot Loader, which it did.  So now I'm back to my original problem - Windows boots fine from Windows Boot Loader, but when I select Ubuntu it never goes to the second screen to allow me to select the Ubuntu version I want to load. The only caveat her is that maybe grub is still floating around somewhere (?) although perhaps recovering the windows boot loader overwrote it.

Sorry for the lengthy explanation, but that is where I'm at and I would love to get my Ubuntu back up and running again.  Thanks.

---

### Post by wilee-nilee on 2011-04-02
Take a look at this, it should get you in shape.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by AeoliX on 2011-04-02
Thanks wilee-nilee - I had somehow not found that page while searching the site for this issue before posting.  I bet one of those solutions will do it.  Thanks!

---

