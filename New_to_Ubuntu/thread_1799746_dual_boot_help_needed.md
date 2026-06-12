---
title: "dual boot help needed"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by rkanth on 2011-07-08
Hi all.

As explained in [this thread]("http://ubuntuforums.org/showthread.php?t=1799161") I have Karmic and am happy. But I also want to install Lucid for LTS.

I have downloaded the ISO and made a usb start-up disk. Unfortunately it is getting stuck at 'ubuntu' screen indeinitely. So, I want to move ahead of 'trial' phase and install it permanently.

Will someone here give me a walk-through of setting up a dual-boot of karmic-lucid on my computer with this ISO?

I want to be with Karmic till I'm comfortable with Lucid and get my settings right.

I backed up the home folder to another, internal, hard disk. Let me also tell you that I don't have a CD writer.

Thanks,
RK

---

### Post by sikander3786 on 2011-07-08
You mean the boot process gets stuck at the Ubuntu logo screen (plymouth) before it even gets to the desktop?

If yes, the first thing to try is 'nomodeset'.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

If that doesn't solve the problem for you, you might want to try a few other parameters also like 'acpi=off' or 'noapic'.

[https://help.ubuntu.com/community/LiveCDBootOptions#Changing](https://help.ubuntu.com/community/LiveCDBootOptions#Changing) the CD's Default Boot Options

It might also be better to check the disc/image for any possible defects.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/LiveCDBootOptions#Main Page Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main Page Options)

Here is a step-by-step guide for troubleshooting a few common installation problems with Ubuntu.

[http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html](http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html)

And if the disc is corrupted and you can't manage a new one, you can try booting the ISO image itself from the Grub menu and install.

[http://ubuntu4beginners.blogspot.com/2011/07/boot-iso-image-using-grub2.html](http://ubuntu4beginners.blogspot.com/2011/07/boot-iso-image-using-grub2.html)

---

### Post by rkanth on 2011-07-08
This may sound a bit silly to you guys, but....

Is it possible to install Lucid into the partition that already has Karmic? Can these two share a single home folder? I know I'm a tech-novice but was wondering...

---

### Post by sikander3786 on 2011-07-08
2 distributions can not exist in the same partition.

Home _partition_ can be shared between different distros but only if you had setup your /home on a separate partition, or you can do it now by moving your /home to a partition but that requires some serious work.

Sharing the /home between different distros brings some problems/hassle alongwith and that isn't what an average user needs.

---

### Post by rkanth on 2011-07-08
Thanks. I went for a clean install. Downloaded all I could remember I did with karmic and am with fingers crossed. Want to live with Lucid till 2013.

---

### Post by sikander3786 on 2011-07-08
Good Luck!

And I hope Lucid will serve you well ;)

---

