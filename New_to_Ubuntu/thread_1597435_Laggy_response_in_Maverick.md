---
title: "Laggy response in Maverick"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by chrwl on 2010-10-15
Hi everyone

Been visiting the forum for a while and have found answers to almost all my questions in the past, but this time I'm stuck.

Installed Ubuntu 10.10 x86 on a Fujitsu Lifebook S7110 (Core Duo, 945GM, Intel Pro Wireless 3945ABG). There is generally a slow response when navigating in the menus and on the desktop. Videos in VLC also pause for a second when I move the mouse. I've tried the usual changes in xorg.conf as indicated for 9.04, but according to the log all those options are ignored. I have used 9.04 in the past, until the 9.10 update broke my install.

Kernel panics occur almost once every 4 times on booting or rebooting (will have to find a log of where it happened). I first thought that these were caused by the wireless card, but even with the WiFi disabled in the BIOS, the kernel panics still occur. I also get a string of > output_poll_execute **ERROR** delayed enqueue failed -125 messages on booting, shutdown and at the command line.

Should I just wait it out and hope for a fix?

---

### Post by makro on 2010-10-19
I don't have kernel panic... but laggy responses very often... I supposed it was a USB issue... but it isn't

sometimes during shutdown I need to press a key 2 or 3 times in a row to complete it!!

---

### Post by makro on 2010-10-21
SOLVED!!

I had to update my laptop's BIOS.
My PC's HP Compaq 6730s with intel GMA. 
Upgrading BIOS solved all the issues

---

### Post by chrwl on 2010-10-25
Update:

Figured out that it is kernel mode-setting causing the trouble. When I disable KMS at boot (i915.modeset=0), the problem goes away, but X refuses to start because user-mode code has been removed from the latest Intel graphics drivers. ](*,)

I am currently using the VESA drivers which give me a nice responsive desktop, no kslowd00* processes running and no kernel panics at boot, but without any acceleration whatsoever.

Where do I find and how can I install an earlier Intel graphics driver? I've tried installing one of the drivers from intellinuxgraphics.org, but can't get it to compile properly.

Oh yes, my BIOS is the latest version available, but I've tried using earlier BIOS revisions with the same results.

---

### Post by elvisramalho on 2010-11-10
I have exactly the same laptop and the same problem.

Found the solution here: [http://www.phoronix.com/scan.php?page=article&item=intel_kms_ums&num=1]("http://www.phoronix.com/scan.php?page=article&item=intel_kms_ums&num=1")

You have to use 10.04 or install the old intel driver in 10.10 so you can use UMS.

I have 10.04 and it works using just the grub parameter.

Hope it helps.

---

### Post by chrwl on 2010-11-14
Thanks, man. Reverted to 10.04 and everything works 100% now.

---

### Post by chrwl on 2012-02-02
I just never learn. Installed 11.10 and the lag is back - the Intel driver is to blame once again. When I force the computer to use the VESA driver, it's as responsive as I've come to expect from Linux.

Can somebody please get a properly-working Intel driver that's compatible with the GMA 950 integrated into the kernel?

---

### Post by elvisramalho on 2012-02-02
Hi,
I'm still using 10.04 in my everyday laptop, stable and fast :) But i've found this:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Say something if it works!

Cheers

---

