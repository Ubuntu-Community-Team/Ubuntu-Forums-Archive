---
title: "GRUB 2 - Want to edit it, but VERY afraid!!!"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-01-19
I have read over and over the main parts in the [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") but I REALLY don't want to mess with anything. I have two operating systems, Ubuntu 9.10 and Windows Vista. All I really want to do is, make the OS titles in the GRUB2 menu actually say their respective names instead of "/boot/sda(0,124433443" etc, etc. and I want to get rid of the memtest+ entries, as well as the recovery entries. Can anyone help me?

Or, would it be easier to revert back to Legacy Grub? I've read a bunch of posts regarding reverting back to Legacy, but many people say don't do it. Help?

---

### Post by itsbrad212 on 2010-01-19
Make a backup of the config file. I don't remember offhand what it is in grub2.

Try this for help:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by drs305 on 2010-01-19
There is an addendum to 'Grub 2 Basics' called 'Grub 2 Title Tweaks' that involves editing the /etc/grub.d/30_os-prober file. If it's too geeky for you, I or someone else could probably help you out if you want to try your hand in editing the script.
[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")

Another alternative is to copy the entire menuentry for Windows and whatever other OS you want from  the 30_os-prober section of  /boot/grub/grub.cfg and pasting it into /etc/grub.d/40_custom, below the existing commented (#) lines. 

Edit the names between the quotes and rename them whatever you wish. Then rename the file *06_custom* so it shows up first on the menu. Next, you remove the executable bit from 30_os-prober file so it won't show your old Windows and other partition Linux installs. Update grub with "sudo update-grub" and you are done. 

The only disadvantage is that by 'disabling' 30_os-prober it won't find updates to Windows or secondary Ubuntu installs on other than the system partition.

Added: The *good* thing is that if you only edit things between the quotation symbols it will be hard to break anything.  ;-)

---

### Post by UnknownFear on 2010-01-19
> **drs305 said:**
> There is an addendum to 'Grub 2 Basics' called 'Grub 2 Title Tweaks' that involves editing the /etc/grub.d/30_os-prober file. If it's too geeky for you, I or someone else could probably help you out if you want to try your hand in editing the script.
[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")

I'm going to go ahead and try this out. Hopefully I get it right. I'll post back with details..... if my computer isn't dead :D

---

### Post by UnknownFear on 2010-01-19
Worked!!! I got rid of the memtest+ and the recovery entries, and fixed the titles a bit. Awesome :) :) :)

---

### Post by drs305 on 2010-01-19
> **UnknownFear said:**
> Worked!!! I got rid of the memtest+ and the recovery entries, and fixed the titles a bit. Awesome :) :) :)

:-)

While it's still fresh in your mind, if there is anything in the tweaks thread that you found confusing or could be improved please feel free to send me a PM about it. I am well aware that this stuff can *look* a bit overwhelming.

Some day we'll have a Grub 2 GUI editor and things will be a lot easier. You'll look back and remember the good old days when you had to learn to do it yourself.

---

