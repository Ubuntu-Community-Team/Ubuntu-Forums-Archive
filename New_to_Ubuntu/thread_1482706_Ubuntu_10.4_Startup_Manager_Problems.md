---
title: "Ubuntu 10.4 Startup Manager Problems"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by doninsa on 2010-05-13
I used startup manager to set Default Operating System to Last Used, but it continues to select Windows XP even though I used Ubuntu last time.  Is there some way to manually edit the configuration file so that the last used operating system is selected?  TIA  Don

---

### Post by cap10Ibraim on 2010-05-13
last used ? I don't have this entry in my startup-manager !
I can choose from a list (see the pic)
for manual configuration [Ubuntu documentation]("https://help.ubuntu.com/community/Grub2")

---

### Post by doninsa on 2010-05-14
> **cap10Ibraim said:**
> last used ? I don't have this entry in my startup-manager !
I can choose from a list (see the pic)
for manual configuration [Ubuntu documentation]("https://help.ubuntu.com/community/Grub2")

I must have an older version of Startup Manager.  Here's what it looks like on my system.

---

### Post by cap10Ibraim on 2010-05-14
I got mine from the software center lately , you may try the new one

---

### Post by ranch hand on 2010-05-14
SUM is not real good with the new grub.  You may want to purge it and look at this link to edit your /etc/default/grub file the right way.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by doninsa on 2010-05-15
> **ranch hand said:**
> SUM is not real good with the new grub.  You may want to purge it and look at this link to edit your /etc/default/grub file the right way.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Thanks for the Grub 2 link. It's just what I needed.

---

### Post by ranch hand on 2010-05-15
Great.

---

