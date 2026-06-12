---
title: "Nomodeset, xforcevesa help"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by Jmgray on 2010-11-16
In order to install Ubuntu 10.04 LTS on my (very) aged HP Pavilion 522n computer, I recieved a blackscreen until I learned I needed to specify nomodeset and xforcevesa when booting from the Live CD by pressing f6 and selecting nomodeset and then adding xforcevesa to the end of the command. After doing so, the install runs just fine, and it successfully puts Ubuntu 10.04 LTS on my hard disk. However, upon attempting to boot from the hard disk, only a blinking white cursor appears and nothing happens. Holding shift to try to bring up grub leaves me with the screen "GRUB Loading..." and a lock up as well. Booting from the cd and running an install again (using the same process) tells me that I have Ubuntu 10.04 on my system, and checking the disk for errors yields nothing. I'm thinking that somehow I need to specify xforcevesa and nomodeset before booting from the hard disk but can't figure out how. Any help?

Also, after another hour's research i've learned that it may have to do with quiet splash. If there's a way to disable that before, during, or after the install for the boot on the hard disk it would certainly be welcome knowledge and worth a fair try.

---

### Post by frowland on 2012-12-04
I have been having similar issues with a fairly ancient a21p Thinkpad laptop.

If I use the Ubuntu 12.10 Live CD and enter xforcevesa on the kernel command line (F6) I can get a nice display and everything works great.

After installation to HDD, however, all attempts to insert xforcevesa into the boot process fail. I have tried modifying the grub loader settings, editing the command line, etc. But every time, the Ubuntu boots with a skewed screen display. I suspect there is a silver bullet that can fix this but I haven't found it yet.

BTW, to stop the splash screen use the nosplash command line parameter.

---

### Post by wildmanne39 on 2012-12-04
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

