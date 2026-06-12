---
title: "URGENT! I can't access Ubuntu!"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-02-27
Ok this morning I went into my recovery system (in Windows XP) to delete the recovery partition to get more space, which didn't work by the way, but that is something I can deal with later.

Now the problem is that my computer just boots into Windows XP automatically without the boot menu, so I can't choose Ubuntu at all.

I'm doing some research to find a solution but it is urgent! I need to get back on Ubuntu!!!

Is there a key that I can hit right when the computer start to change that or where could I go in Windows to fix this?

I booted the livecd to check my menu.lst in grub and it seems normal. It looks like the Windows boot manager (is it the correct name?) took over and I'd like grub to be the default one!

Thanks!

---

### Post by taurus on 2009-02-27
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by kestrel1 on 2009-02-27
> **taurus said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Just what I was about to suggest.

---

### Post by Xiong Chiamiov on 2009-02-27
While the above solution is most certainly a valid one, and doesn't require anything beyond your Ubuntu cd, I personally find it easier to use [Super Grub Disk](http://www.supergrubdisk.org/).

Note: Their website seems to be down atm, but trust me, it exists!

---

### Post by theozzlives on 2009-02-27
You'll have to re-install GRUB to your MBR, all the times I've seen it I've never printed it but all you did is re-write the MBR no biggie... I'll check my tech manuals and get back to you.

---

### Post by sylvainrb on 2009-02-27
@taurus: Thanks a lot! It works now.

Thanks to the others as well for the prompt responses.

Also does anyone know why it happened? Or is it just because Windows decided so? Haha

---

### Post by kestrel1 on 2009-03-02
Must have been something in the recovery system. If you actually booted in to a recovery console, what commands did you use.
Basically though, the MBR got overwritten by 'useful' :) Windows.

---

### Post by sylvainrb on 2009-03-02
I didn't type in any commands. I just chose the option to delete the recovery partition and the computer just rebooted into the recovery console.

---

### Post by kestrel1 on 2009-03-03
It was probably during the delete process that the MBR was overwritten, it probably noticed that the MBR didn't look right for Windows, so decided to help you out :-)

---

