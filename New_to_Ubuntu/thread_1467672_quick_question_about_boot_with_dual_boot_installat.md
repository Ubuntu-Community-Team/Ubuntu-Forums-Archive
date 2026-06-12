---
title: "quick question about /boot with dual boot installations"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by sleepee on 2010-04-30
ok, so i have a quick question about this /boot directory.
i heard that having a separate /home and /boot directory is safer, more convenient, etc.. so for my ubuntu 10.04 upgrade, i decided to do a clean install to have those separate.  also because i plan on triple booting with mint and opensuse also, and it seems like it's more convenient.

so i went ahead and wiped out my karmic install..
then i started chopping up and partitioning the HD, i created 5 extended partitions:  3 separate /root for each OS (ubuntu, mint, and opensuse), one /home, and one /boot.

so i install ubuntu first, and everything goes well.. i even reboot and find that i don't have that grub problem that i heard about with dual booting lucid (forgot to mention i also have a Windows 7 install as a primary partition).   great!
anyway, so my confusion is with installing the next OS's: mint and opensuse.
this is where my noobness really shows.  lol
when i install mint, i go to the advanced partitioning so i can tell it to use the partition i had set apart for it for its / directory.  fine.
then i specify the /boot directory i had made so it could use that. then it hits me with this:

> The file system on /dev/sda10 assigned to /boot has not been marked for formatting.  Directories containing system files (/etc, /lib, /usr, /var, ...) that already exist under any defined mountpoint will be deleted during the install.

Please ensure that you have backed up any critical data before installing.

now when i see that, i get nervous, because i don't want wipe out the /boot directory and have my grub screwed up so that it won't see my ubuntu and windows..  also i don't want that to happen when i install opensuse..
so i guess my question is:  will formatting the /boot directory when installing mint affect grub?? or will it still see all the other OS's i have??

also, another question that's related..
can i also tell mint and opensuse to use my /home directory without having to format that too???
because if i have to reformat the /home every time i install a new OS, it kind of defeats the purpose of why i wanted a separate /home in the first place..

thanks in advance...
oh, and sorry for making this "quick question" so long  lol!!

---

### Post by swoll1980 on 2010-04-30
edit: misunderstood.

---

### Post by sleepee on 2010-05-01
ahhhh  thanks for the quick reply..  and sorry for the noob question. i'm not too familiar with installing more than one linux distro at a time.  this is really my first time.
thanks again for clearing that up..

btw, just another question out of curiosity...
if i name my home folder in my mint install the same as my ubuntu home folder name (/home/sleepee), will it just save everything under the same folder??  and can that be problematic???

or do i have to have separate /home/username for each distro i install??

---

### Post by 4Orbs on 2010-05-01
You already have grub working well between Ubuntu and Windows, so you don't want to screw up a good thing by permitting the other two systems to overwrite the boot loader. If this were my system I would keep Ubuntu in control of grub regardless of any other installations or re-installations. I'm not a grub guru, but "I think" you keep Ubuntu in control by having each subsequent system install it's bootloader inside it's own root partition only. Then after it is installed, you go into Ubuntu and run update-grub. That way Ubuntu will simply re-detect the newly installed additional system and add it to the already existing grub menu. I could be completely wrong in my understanding of how these things work... so my only real advice is to not do anything until you have plenty of other posts on this thread from which to draw your final conclusion.

---

### Post by oldfred on 2010-05-01
You cannot share boot or /home without huge complications. The only one's that need a separate /boot are those with old BIOS that have memory limits where the boot loaders have to be inside the first 137GB. (Smaller numbers for even older). Kernel versions and configurations will be different with each install so each install should have its own boot.

/home can be shared only if you create new users for each, which defeats most of the reason. You can do some setting to share, but I find it easier to create a shared data partition. Data has no system specific configuration files so it is easy to share. Each system may have different settings for the same program as it may not be the same version. 

How to Multi-boot (Maintain more then 2 OS) 
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by sleepee on 2010-05-01
> **4Orbs said:**
> You already have grub working well between Ubuntu and Windows, so you don't want to screw up a good thing by permitting the other two systems to overwrite the boot loader. If this were my system I would keep Ubuntu in control of grub regardless of any other installations or re-installations. I'm not a grub guru, but "I think" you keep Ubuntu in control by having each subsequent system install it's bootloader inside it's own root partition only. Then after it is installed, you go into Ubuntu and run update-grub. That way Ubuntu will simply re-detect the newly installed additional system and add it to the already existing grub menu. I could be completely wrong in my understanding of how these things work... so my only real advice is to not do anything until you have plenty of other posts on this thread from which to draw your final conclusion.

wow.. good thing i just re checked this thread..  i was about to format the /boot partition...
but what you say seems logical enough though..  i'm tempted to try it now, but i'll wait a little while longer...
thanx

---

### Post by swoll1980 on 2010-05-01
If you are Dual booting like you say in the thread title you have nothing to worry about. If you are triple booting it would break your other install if you followed my advice from before.

---

### Post by sleepee on 2010-05-01
> **oldfred said:**
> You cannot share boot or /home without huge complications. The only one's that need a separate /boot are those with old BIOS that have memory limits where the boot loaders have to be inside the first 137GB. (Smaller numbers for even older). Kernel versions and configurations will be different with each install so each install should have its own boot.

/home can be shared only if you create new users for each, which defeats most of the reason. You can do some setting to share, but I find it easier to create a shared data partition. Data has no system specific configuration files so it is easy to share. Each system may have different settings for the same program as it may not be the same version. 

How to Multi-boot (Maintain more then 2 OS) 
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

wow.. thanks for that info.  i'm not too familiar with multi-booting, so i'm going to read those threads before i do anything else..  but it seems like i'll have to repartition my HD again and just have all the distros have they're own /boot right??
anyway, it seems like i'm going to have my hands full with this since i don't know much about how bootloaders work..
thanks again..

---

### Post by sleepee on 2010-05-01
> **swoll1980 said:**
> If you are Dual booting like you say in the thread title you have nothing to worry about. If you are triple booting it would break your other install if you followed my advice from before.

yea, i'm actually triple booting, maybe even quad booting, if i can figure it out...  sorry about that..
i've done dual bootings before and they're pretty easy.. this is my first time trying multi booting more than 2 OS's though..

---

### Post by oldfred on 2010-05-01
While this is older and uses old grub it shows some of the planning required to boot multiple systems.

chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

I would keep boot inside the root partition where possible. New installs of win7 and I think Fedora require separate boot partitions.

I have 3 versions of Ubuntu. Since I am upgrading from the same software I use the same home as I upgrade, but do not plan on using the old version once converted to the new as the /home settings may not work. I would only boot the old version as an emergency or to find some obscure setting that I forgot to convert.

---

### Post by sleepee on 2010-05-01
> **oldfred said:**
> While this is older and uses old grub it shows some of the planning required to boot multiple systems.

chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

I would keep boot inside the root partition where possible. New installs of win7 and I think Fedora require separate boot partitions.

I have 3 versions of Ubuntu. Since I am upgrading from the same software I use the same home as I upgrade, but do not plan on using the old version once converted to the new as the /home settings may not work. I would only boot the old version as an emergency or to find some obscure setting that I forgot to convert.

thanks for all this info...  that last one really helps out a lot with the examples.  i definitely need to read up on it, but now that i know that multibooting is a little more complex than i thought, i think it might not be the best option for me..
sorry that i might not do this multibooting after you gave me all this help, but i guess now that i know what it really is, i think just using virtual box to play around with opensuse and mint might be my best choice...
thanks a lot though.

---

