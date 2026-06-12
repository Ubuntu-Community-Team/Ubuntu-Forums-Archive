---
title: "Alert! /dev/sda1 does not exist"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by felipedesiqueira on 2011-02-03
I am attempting to install a fresh ubuntu 10.4 LTS and receive the error:

Alert! /dev/sda1 does not exist dropping to shell!

I previously had the error tell me the UUID of the drive does not exist, I proceeded to change /etc/default/grub by uncommenting the value...
GRUB_DISABLE_LINUX_UUID=true

This fix is noted here help.ubuntu.com/community/KarmicUpgrades.

I can boot into recovery mode and see that my root is in /dev/sda1.  Grub is now pointing to /dev/sda1 to find the root.

Anyone have any ideas?

---

### Post by oldfred on 2011-02-03
Lets see what this shows:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

