---
title: "Messed it up-install hangs-please help"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by germanix on 2011-03-04
Hi all. Being my usual stupid self, I messed about with the Linux Mint Debian Edition and broke my system. I am now trying to re-install Ubuntu 10.10 but the live disk starts to load and then hangs up. I tried various life disks that I know are all ok but none will install.
I booted with  a GParted live disk and totally re formatted the drive but that did not help.
Any ideas?

(Edit) I now tried various installations all with the sam problem. The Mint Debian version hangs in the boot sequence on the line: Starting Gnome Display Manager gdm3
I assume all of the other distro`s hangs on the same line but is not visible.
Could this be a problem with the Gnome display and how would I fix that?
At the moment I cannot install anything!

---

### Post by sikander3786 on 2011-03-04
Mint or a messed up install has nothing to do with CD/USB boot problems. It is something else, might be you need to put in some boot parameter (needed in many cases with newer Ubuntu versions).

Can you please explain where it hangs while the boot process? If at the Ubuntu logo screen, you might need to put in the 'nomodeset' parameter or the 'acpi=off' from F6 options at the Main Page. See here.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

For known common installation problems,

[http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html](http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html)

Once we know your exact problem and any error messages (if any), we'll be able to help more efficiently.

---

### Post by germanix on 2011-03-04
Up until yesterday I was running Ubuntu on this machine with no problems. I installed LMDE to try it out (as sole OS) That did not work for me (no wlan, could not update without problems)
Decided to re-install Ubuntu.
Ubuntu live disk starts the operation, begins to load then just stops half way through the boot process. No error messages, just the Ubuntu Logo
Also tried other distro live disks, all with same result!

---

### Post by sikander3786 on 2011-03-04
So you are trying from CD-ROM discs, right? Can you rule out the fact that your CD-ROM drive might actually be malfunctioning?

Did you try with a USB drive instead?

---

### Post by germanix on 2011-03-04
Yes I can. I can boot for example from a Gparted live disk.

(Edit) The LMDE also boots. It hangs at line (starting Gnome Display manager) for some minutes, but then continues the boot process. Mint and Ubuntu just hangs and does not continue with the boot.

---

### Post by sikander3786 on 2011-03-04
I would then suggest to run a memtest and test your RAM modules. They might be ok but who knows?

And there isn't any problem with GDM from a Live CD in my notice at least. I would say, you RAM is worth checking and also the graphics card.

---

### Post by germanix on 2011-03-04
I thank you all for your help and advice. The only way I could get my system up and running again was to use the system restore CD with Windows XP. Never thought I would ever install Windows again. Well it restored the system and I then installed Mint 10 over Windows as sole OS. Now all is back to normal and working fine.
I guess LMDE was not to be on my hardware. Would have liked it but now I am to scared to even go near it again.

---

