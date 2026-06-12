---
title: "Grub not showing/Automatically boots to ubuntu"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by IamFuzzles on 2011-07-05
I recently installed Ubuntu onto my new netbook (eee pc from Asus, 1001px). I partitioned it to be ready to boot both FreeBSD and Windows 7, but haven't installed either. However, whenever I boot, it merely boots straight to ubuntu. I've tried executing grub-install /dev/sda but it's done nothing. I've searched everywhere, but haven't found a thing. Thank you in advance for the help.

---

### Post by alphacrucis2 on 2011-07-05
> **IamFuzzles said:**
> I recently installed Ubuntu onto my new netbook (eee pc from Asus, 1001px). I partitioned it to be ready to boot both FreeBSD and Windows 7, but haven't installed either. However, whenever I boot, it merely boots straight to ubuntu. I've tried executing grub-install /dev/sda but it's done nothing. I've searched everywhere, but haven't found a thing. Thank you in advance for the help.

If there are no "foreign" os's present, the default ubuntu grub setup doesn't display the boot menu. You can force it by holding down the shift key at boot time. Once the other OS's are installed and you have run grub-update under ubuntu to detect them, the behaviour will change and the menu should be displayed by default. Have a look at the ubuntu grub2 community doc for more info.

 However be aware that if you install any version of windows after grub has been installed, the windows installer will overwrite the MBR and therefore blow grub away. To get grub2 back you can always reinstall it from the live CD.

---

### Post by IamFuzzles on 2011-07-05
Thank you!

how would I install it from the live cd? through a similar terminal command?

Also, I tried the update-grub command, it said it detected an unknown linux format. I rebooted and it loaded grub this time, but the FreeBSD update isn't listed. Any ideas?

---

### Post by alphacrucis2 on 2011-07-06
> **IamFuzzles said:**
> Thank you!

how would I install it from the live cd? through a similar terminal command?

Also, I tried the update-grub command, it said it detected an unknown linux format. I rebooted and it loaded grub this time, but the FreeBSD update isn't listed. Any ideas?

There are many guides out there on installing grub2 from live CD eg


[URL="http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html"]http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html
[/URL]

You may also like to read the grub2 community doc:

[URL="https://help.ubuntu.com/community/Grub2"]https://help.ubuntu.com/community/Grub2
[/URL]

Never used BSD. A quick search on the BSD issue came up with this. If it doesn't help, you may need to check through whtever articles you can find.

[http://ubuntuforums.org/showthread.php?t=1664557]("http://ubuntuforums.org/showthread.php?t=1664557")

---

### Post by grahammechanical on 2011-07-06
I am confused. First you say

> haven't installed either

Then you say

> the FreeBSD update isn't listed

Does this mean that you have install FreeBSD since your first post? What format did you use for the FreeBSD partition. May be this is the unknown format detected by the update-grub command. And for this reason FreeBSD is not appearing in the Grub menu. I am just guessing.

Regards.

---

### Post by IamFuzzles on 2011-07-06
> **grahammechanical said:**
> I am confused. First you say



Then you say



Does this mean that you have install FreeBSD since your first post? What format did you use for the FreeBSD partition. May be this is the unknown format detected by the update-grub command. And for this reason FreeBSD is not appearing in the Grub menu. I am just guessing.

Regards.


I did install FreeBSD since my first post, and yeah, I assumed that's what it was detecting. I installed it on /dev/sda3

---

