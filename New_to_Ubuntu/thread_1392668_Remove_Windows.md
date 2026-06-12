---
title: "Remove Windows?"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by MrNatural on 2010-01-28
I'm a new Ubuntu user (Karmic Koala), and now have Ubuntu running the way I want it to (well, almost - I'm still grappling with sound issues).

But my question is about removing Windows completely from my dual boot setup. Could someone point me to a simple guide on how to do this?

Thanks!

Alan

---

### Post by phillw on 2010-01-28
> **MrNatural said:**
> I'm a new Ubuntu user (Karmic Koala), and now have Ubuntu running the way I want it to (well, almost - I'm still grappling with sound issues).

But my question is about removing Windows completely from my dual boot setup. Could someone point me to a simple guide on how to do this?

Thanks!

Alan
Hi and welcome to the forums,

A nice easy way, is to use the LiveCD and GParted within that to format the Win partition as ext4.

You can then either use the partition as general storage, or better, use it to make a seperate /home directory.

Once you've formatted the partition, when you boot back to your system, Win will still show as a boot option - Select Ubuntu, drop to terminal and issue
```
sudo update-grub
``` to get grub to re-check what operating system(s) you have.

Regards,

Phill.

---

### Post by audiomick on 2010-01-28
Hi.
I found this
[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)
in the documentation.

However, it is still talking about using grub legacy, whereby Karmic 9.10 (from a fresh install) uses grub2 (if it is an updated 9.04, it will still have grub legacy)

For correcting your grub after the changes, phillw has given you advice.
You can read about it yourself here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by MrNatural on 2010-01-28
Many thanks!

Alan

---

### Post by MrNatural on 2010-02-01
I used GParted to format the Win partition as ext4, and then used Terminal to issue sudo update-grub.

Then I used Terminal again to modify /boot/grub/menu.lst in order to remove Windows from the boot menu- only to be told that there's no such file in my system!

How can that be? I can see a boot menu so that file must exist. Am I missing something very obvious here?

Alan (feeling very noobish right now)

---

### Post by howefield on 2010-02-01
No menu.lst in Grub2

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by MrNatural on 2010-02-01
Thank you!

Alan

---

