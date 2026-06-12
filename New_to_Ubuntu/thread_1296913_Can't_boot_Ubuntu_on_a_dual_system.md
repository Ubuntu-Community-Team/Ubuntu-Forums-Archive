---
title: "Can't boot Ubuntu on a dual system"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by stuckagain on 2009-10-21
Hi,
 
I have a dual-booting system with Windows XP and Ubuntu 8.10 . The Windows startup files got corrupted (possibly by malware from the net), and I can't boot windows anymore. My problem is I can't boot Ubuntu either. The (ubuntu) startup fails saying that Windows did not shutdown cleanly. Now, till I sort out the Windows startup with a bootdisk, I want to use Ubuntu. How can I do that?
 
I am wondering whether preventing the automatic mounting of the windows partition (to "host" directory) will enable Ubuntu to boot cleanly. How do I do this ? Is it by issuing a "hide *partition-name*" command from GRUB command-line?
 
Thanks.

---

### Post by MelDJ on 2009-10-21
this is assuming you installed with wubi. 
boot from the windows cd and go into recovery mode. then run chkdsk. then restart and you should be able to boot into ubuntu.

---

### Post by stuckagain on 2009-10-21
Thanks for the prompt reply.  Yes I installed with wubi. But I don't have a Windows CD - my Thinkpad came with XP pre-installed...
 
can i not boot ubuntu somehow without touching windows?

---

### Post by MelDJ on 2009-10-21
check this out: [http://www.computerhope.com/boot.htm](http://www.computerhope.com/boot.htm)

---

### Post by Zalbor on 2009-10-21
I'm not entirely sure, but I think that if you have a windows license (on the sticker on your computer, probably) it's not illegal to download an OEM windows cd and use your product key to install. You could probably find drivers on the manufacturer's website.

---

### Post by MelDJ on 2009-10-21
> **stuckagain said:**
> Thanks for the prompt reply.  Yes I installed with wubi. But I don't have a Windows CD - my Thinkpad came with XP pre-installed...
 
can i not boot ubuntu somehow without touching windows?

the problem is windows was turned off improperly. so we must run a chkdsk to scan and fix errors. after that, ubuntu will boot :)

---

