---
title: "GRUB command prompt"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by nations111 on 2010-01-27
Maybe a simple and much posted problem but used wubi to install 9.10, installed fine but after selecting ubantu after startup am just presented with the GRUB command prompt. Absolutely new at this so any advice appreciated

---

### Post by oldfred on 2010-01-27
I copied this from another thread:

[http://ubuntuforums.org/showthread.php?t=1376845](http://ubuntuforums.org/showthread.php?t=1376845)
wubi:
Type this at "grub sh>" prompt:

set Path=/ubuntu/disks/root/disk
search -f --set=Root ${Path} 
probe -u (${Root})  --set=UUID   
linux /vmlinuz root=UUID=${UUID} loop=${Path}  ro
initrd /initrd.img
boot

Once booted in Wubi, open a terminal and type

sudo update-grub

Hopefully this will take care of the problem.

---

### Post by meierfra. on 2010-01-27
> I copied this from another thread:

oldfred:  When did you copy this?  I edited that post  a  few  hours after I posted it, since the probe command is not available  in Wubi. Also later in that thread I realized that "update-grub" only solves the problem in some of the cases. 


nations111: Your problem is most likely caused by a bug in Grub 2. See this link for more details and how to fix it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by oldfred on 2010-01-28
meierfra.
I am glad you corrected me on this. I like to copy commands both for my use and possibly as suggestions for others. I have not used wubi but saw a lot of issues, so I copied your original and must have done that right after your first posting. I do find that a lot of times users do not like to follow links but I usually like to provide links as they often will include updates.

Nations111 - I hope you have seen the corrections and let us know how it works.

---

