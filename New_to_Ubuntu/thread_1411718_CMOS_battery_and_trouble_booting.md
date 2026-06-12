---
title: "CMOS battery and trouble booting"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by NewbuntuUser777 on 2010-02-20
This may be more of a general computer and less of an ubuntu problem, so I apologize in advance if that's the case.

Running ubuntu 9.10 on an HP pavilion machine, on shutdown the computer screen goes all crazy, then won't boot past bios splash screen anymore. After plugging and unplugging various components, ram, I eventually remove and reinsert the CMOS battery.

Now it boots into grub, BUT it can't mount file system!

After some fiddling, I figure out that if I set the date to be a future date in the bios setup on reboot, I can get the filesystem to mount after 
ubuntu runs a filesystem check.

So my question is how do I get it to boot without setting the bios clock 
forward to the future?

Also, is this an ubuntu issue, a bios issue, ongoing CMOS battery problem?

---

### Post by mcduck on 2010-02-20
Are you dualbooting, or do you only have Ubuntu on that machine?

If you only have Ubuntu, then it most likely assumes your CMOS clock to run in UTC time, so dependening on your time zone setting the CMOS time to your local time would actually result in compeltely wrong time in Ubuntu. And wrong tme might cause probelms mounting filesystems, as file creation times etc. migh appear to be in future etc...

So, if you only have Ubuntu on that machine try setting the CMOS time to UTC time instead of your local time.

---

### Post by egalvan on 2010-02-20
Can you tell us exactly what errors it is showing?

---

