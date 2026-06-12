---
title: "Help! Ubuntu 10.04 stuck on grub&gt; after disabling/re-enabling primary HD in Bios"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by niM_xaM on 2010-11-21
Help Guys,

My Ubuntu 10.04 now boots straight into grub>_ (grub prompt?) and would just stop at there. 

This happens after I disabled+re-enabled the primary hard drive (on which my Ubuntu 10.04 was installed).... I was experimenting with something and now can't recover.. Any idea what went wrong? or how to fix it? .. please help guys - thanks bunch in advance! 

niM_xaM

---

### Post by Daveth on 2010-11-21
you might want to scoot through to the back end of this guide and see what matches what you can find to your problem. Should be easy to recover.

[HTML]https://help.ubuntu.com/community/Grub2[/HTML]

---

### Post by oldfred on 2010-11-21
Can you manually boot?

Manual boot:

Adjust drive, partition to your install - example is sdb3 or hd1,3:
sh:grub>ls
#If on (hd1,3) or sdb3
sh:grub>ls (hd1,3)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,3)/vmlinuz root=/dev/sdb3
sh:grub>initrd (hd1,3)/initrd.img
sh:grub>boot

---

### Post by niM_xaM on 2010-11-22
Thanks guys, I got it back up and running already. Oldfred, no I couldn't do manual booting, the grub>_ prompt did not even recognize the ls command. I studied the page provided by Daveth and finally followed the steps to reinstall GRUB2 files from LiveCD. 

Now I'm back to my old desktop again. Yay! 

Thanks for the quick reply guys

niM_xaM

---

### Post by niM_xaM on 2010-11-22
[SOLVED] Thanks guys, I got it back up and running already. Oldfred, no I couldn't do manual booting, the grub>_ prompt did not even recognize the ls command. I studied the page provided by Daveth and finally followed the steps to reinstall GRUB2 files from LiveCD. 

Now I'm back to my old desktop again. Yay! 

Thanks for the quick reply guys

niM_xaM
*) Btw, how do you mark this thread as [SOLVED]?

---

### Post by atomizer on 2010-11-22
see oldfred's signature: use "thread tools" to mark as "solved"

---

