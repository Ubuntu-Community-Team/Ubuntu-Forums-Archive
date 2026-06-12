---
title: "Help with an external Harddrive"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Jonker on 2011-02-28
Hi there,
I wanted to install Ubuntu 10.10 on external harddrive. So I put in the Live-CD, and installed it on the Harddrive. But now, I realised, that Ubuntu must have changed the MBR on the internal hardrive, because if the external HD isn't connected, it gives me a "Grub error". So the Laptop is not usable without the external HD.
My idea was: If the external Harddrive is connected, then boot from the Harddrive ( I have that option in the BIOS), but if it isn't connected, then boot Vista. 
Can you please halp me to get the Laptop working without the external HD?

---

### Post by ZeroAdam on 2011-02-28
Was your laptop running Vista to begin with? Are you trying to get back to Vista?

If I'm re-reading you right, you want to boot to Vista under normal circumstances. I believe the FIXMBR windows command accomplishes this. You'd need your Windows installation disk to boot to a command prompt I believe.

---

### Post by Jonker on 2011-02-28
Yes, the Laptop was running Vista at first. Ill try try the fixmbr.

---

### Post by Jonker on 2011-02-28
Hi there,  I just noticed, that I dont have the Install Cd, because Vista was pre-installed. What can I do?

---

### Post by Jonker on 2011-02-28
ok, I need to corrct myself: after booting it gives me: error: no such device : ... grub rescue> the I put the ls command grub rescue> ls (hd0)(hdo,msdos3)(hd0,msdos)(hdmsdos1) I hope it helps you

---

### Post by beew on 2011-02-28
At one point during the install you have to specify that the bootloader be installed in the external drive. As far as I remember this doesn't happen by default (you have to choose "advanced" at some point)
I have done this many times(with 10.04 and 10.10) it never messed up the internal system. But if you want to be safe you can disconnect the internal drive first next time.

I am sorry, can't help you with the problem of getting back to Vista without a disk, but I think the fixmbr command works only with XP even if you have a disk, with Vista and Win7 it is a bit different.

Hope someone more knowlegable will help you to get your system back.

---

### Post by hansolo4949 on 2011-02-28
Well, you have two options, one that is easy, if you have the right disk, one that is hard(er) but will work, regardless. The first option is to boot from a vista (and I think win 7) recovery cd. If you don't have one, you can always ask a friend if you can borrow it:). The second option is to install GRUB on the internal hdd, so that the error messages go away. I do not have experience with doing that, but after a quick google search, ```
grub-install /dev/hda
``` may help. Now, please do not do that until someone else says it is okay, since I may just be getting you into deeper trouble. But after installing GRUB, you should be fine!

---

### Post by Roger Allott on 2011-02-28
> **Jonker said:**
> Hi there,
I wanted to install Ubuntu 10.10 on external harddrive. So I put in the Live-CD, and installed it on the Harddrive. But now, I realised, that Ubuntu must have changed the MBR on the internal hardrive, because if the external HD isn't connected, it gives me a "Grub error". So the Laptop is not usable without the external HD.
My idea was: If the external Harddrive is connected, then boot from the Harddrive ( I have that option in the BIOS), but if it isn't connected, then boot Vista. 
Can you please halp me to get the Laptop working without the external HD?

That is exactly the arrangement that I wanted a few years ago, and managed to get. The essential aspect of the installation was to take out the internal hard disk beforehand so that grub would only load onto the external HD (and thus only be activated when the external HD was attached at boot up).

---

### Post by Jonker on 2011-03-03
Hi there,
I posted my problem in the General part of this forum, because I thought, that it isn't really a beginner Question. And I found help there:

[http://ubuntuforums.org/showthread.php?t=1697219](http://ubuntuforums.org/showthread.php?t=1697219)

Thank you for trying to help me!!!

---

### Post by beew on 2011-03-03
> **Roger Allott said:**
> That is exactly the arrangement that I wanted a few years ago, and managed to get. The essential aspect of the installation was to take out the internal hard disk beforehand so that grub would only load onto the external HD (and thus only be activated when the external HD was attached at boot up).

There is no need to remove the internal hard disk, just make sure you install the bootloader in the external one.

---

### Post by 3177 on 2011-03-03
well I was going to give you a link to a thread that this was solved on.... but it was yours so I see your opening multiple threads. So yeah, dont do that.

---

