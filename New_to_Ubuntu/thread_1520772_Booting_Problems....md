---
title: "Booting Problems..."
date: 2010-06-30
forum: New to Ubuntu
---

### Post by Rybandt on 2010-06-30
I can't seem to boot WITHOUT deleting quiet splash and adding irqpoll... Also when I DO replace it, everything works, just when entering text or scrolling pages it seems slow. I've been trial and erroring my way through linux for 20 hours now. Almost there....Is there a way to PERMANENTLY DELETE the quiet splash and PERMANENTLY ADD irqpoll? I need a complete idiots guide because I don't understand "Sudo this and tarball that"... Please help! Also, if you know how to get my wireless card running that would be awesome. 
rtl8192se

---

### Post by oldfred on 2010-06-30
I am assuming grub2 as the instructions fro grub legacy are totally different( eidt menu.lst). You just need to edit grub file and run update to copy it permanently to the menu.

gksudo gedit /etc/default/grub 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

After all updates

sudo update-grub

See section 5 for details
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

