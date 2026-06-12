---
title: "Grub prompt after update"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by petewaddy on 2010-11-28
I have been running ubuntu 10.10 for a while now, it was orginally installed via the wubi installer onto a vista laptop.

Recently the update manager had installed 70MB of updates and restarted, 
Now when selecting the ubuntu choice from the menu, rather than a list of availabe kernels is now just says
GRUB>.

I think that a part of the update has changed something, but I am at a loss of what to do now, having had virtually no experience of GRUB.

Can I manually boot from the GRUB prompt and then can I permantely fix this error?

I have read about problems with a recent GRUB update and WUBI, but it seems to mention upgrading from 10.04 to 10.10, and not updating 10.10 itself, so I was relucant to follow the corrections in case I made it worse

---

### Post by sikander3786 on 2010-11-28
See if this one helps.

[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

---

### Post by petewaddy on 2010-11-28
After copying the c:\ubuntu\winboot\wubildr file over the c:\wubildr file, 

1) The very first time ubuntu was selected, there were some flashing characters and a line that said error file not found, with a flashing cursor below, but nothing could be entered.

2) Now, after powering down when you press the ubuntu entry, the laptop resets and comes back  to the startup menu, with a choice of windows or ubuntu.

---

### Post by philinux on 2010-11-28
Have a look at the troubleshooting section.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by petewaddy on 2010-11-29
The following link, which uses the live CD to mount windows, then the wubi installation, and edit the grub.cfg file worked for me.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Everything is now working as it was.

---

### Post by drs305 on 2010-11-29
Glad you solved your problem.  :-)

Just to confirm the symptoms and solution since so many users are having the same problem this month.

You boot to the Windows menu, choose Ubuntu and then ended up at the "grub" prompt. You then mounted Windows, then the Ubuntu root.disk, and removed the top portion of the grub.cfg file (everything above the first menuentry). Saved the file, rebooted and then everything worked again.

Is that correct?

Also, have you tried running "sudo update-grub" since you fixed the problem? If so, what was the result?

Also, it would help a lot of users looking for the answer to this problem if you would mark it SOLVED via the 'Thread Tools' link at the top right of the first post.

Thanks for your feedback.

---

### Post by petewaddy on 2010-11-29
Yes, after an upgrade of some files in 10.10 via update manager which requested a restart.
I booted to the windows menu, selected ubuntu and ended up with the GRUB prompt.
I then copied the file c:\ubuntu\winboot\wubildr file over the c:\wubildr file, which then resulted in a reset when I selected the ubuntu option.
I then used a live 10.10 cd to boot into ubuntu and once I had a terminal window open, mounted, windows, then wubi,
then edited grub.cfg, removing all the lines above the first menuentry item, then saved that, restarted and I now when I select the ubuntu option I get the list of kernels I  had before and everything seems to work ok.

I have not tried sudo update-grub since fixing it.

---

### Post by petewaddy on 2010-12-01
Just a quick update, today update manager pulled down 170Mb of updates, and after a restart, from the windows menu, selecting ubuntu brought about a system reboot.

Luckily I know what to do, 3 minutes later after booting from the live CD, I had mounted windows, then wubi and then re-edited the grub.cfg file as before and now everything works ok again.

---

