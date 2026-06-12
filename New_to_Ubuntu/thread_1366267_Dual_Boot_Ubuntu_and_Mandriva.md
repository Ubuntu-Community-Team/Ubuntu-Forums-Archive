---
title: "Dual Boot Ubuntu and Mandriva?"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by TBABill on 2009-12-28
I know it is possible and probably easy to do so, but has anyone dual booted 2 different Linux versions that also come with different boot loaders? Here's the problem I am trying to figure out....
 
I want to dual boot Ubuntu 9.10 and Mandriva 2010. I like both and want to test back and forth on the same machine (booting into each). Ubuntu uses Grub2 and Mandriva uses Grub. What conflict will this cause? Should I just partition and install the Grub loader with Mandriva since Grub2 may not recognize Mandriva? Should this be a concern?

---

### Post by Ben Wright on 2009-12-28
I believe this forum post addresses your question: [http://forums.scotsnewsletter.com/index.php?showtopic=30224](http://forums.scotsnewsletter.com/index.php?showtopic=30224) (google: grub 2 boot mandriva). Thanks.

---

### Post by kansasnoob on 2009-12-28
I knew from following Karmic development that ranch hand got Mandriva to boot with grub2:

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

I had a heck of a time getting openSUSE or Fedora to play well with grub2 so I ended up having to revert to using legacy grub in those cases.

---

### Post by TBABill on 2009-12-28
Ben, thank you. That's the post that created my question because it solves the problem for someone using dual hard drives, but not one hard drive partitioned to dual boot. How do you create settings that will not affect either OS? And which Grub is the one of choice that will boot either? From the post it looked like they had chosen Grub over Grub2.
 
I just don't want to overwrite my Grub2 when I install Mandriva because I believe it will force an install of Grub. I'm not experienced enough to know how to force or use one bootloader over another during an install.
 
Any help on it is appreciated...or just clarification if I didn't correctly understand the posting from scotsnewsletter above.

---

### Post by ffi on 2009-12-29
I would use mandriva's grub, it looks prettier and when something messes up you can use the mandriva control center to fix things easily rather than hope grub2 will do it automatically for you (it never does with my mandriva partition) in the end I decided to complete remove grub from ubuntu (as ubuntu kernel updates places grub2 back again on the bootsector, which made mandriva unbootable)

Anyway mandriva's installer has an option to install grub, lilo or no bootloader at all but I don't recommend using ubuntu's grub2 for reasons above.

---

