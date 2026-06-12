---
title: "How to reset GRUB2 to original installation default from Live CD"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by virtualsamana on 2011-03-02
Hi,

I tried unsuccessfully to customize GRUB. I set timeout to 0 and now it only loads the first OS kernel without the GRUB menu appearing. I did this because I mistakenly believed that if I pressed shift the GRUB menu would appear. Anyway, now I would like to reset grub to default. Is there a way to do this. 

Since GRUB doesn't even appear, windows 7 loads by default. Can I use the live CD to reset GRUB settings? If so, how?

Thanks

-------
Ubuntu 10.4
Windows 7

---

### Post by Foxheadz on 2011-03-02
Google is your friend:[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by virtualsamana on 2011-03-02
Thanks for the reply. I actually tried doing that. I  successfully reinstalled grub but it didn't seem to reset the settings. I still am unable to see a grub window. It states that grub is loading but then immediately starts booting windows without giving me the option to choose an OS.

---

### Post by wilee-nilee on 2011-03-02
I think you have to purge and then reinstall grub to in.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Foxheadz on 2011-03-03
Yeah i agree with wilee, also if your looking for a way to customize your boot selection screen i would suggest looking into burg it's exactly like grub but allow you to select a theme for the selection screen. [https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg) and burg manager which lets you easily edit it [http://gnome-look.org/content/show.php/Burg-manager?content=127497](http://gnome-look.org/content/show.php/Burg-manager?content=127497)

---

### Post by virtualsamana on 2011-03-04
Thanks guys. I purged and reinstalled grub with Rescatux. If I need to reinstall again I will follow the instructions from drs305 thread. Working well now. I will also look into burg. :D 

Should I mark the thread as solved or does a mod do that?

---

