---
title: "grub error 17 unable to boot"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by kumaresan89 on 2009-10-15
hi i have installed Windows Xp and Ubuntu 9.04 (dual boot) .I deleted a partition in Xp but i cannot boot now because it is showing an error message 
```
Error 17
```how to correct it.
thanks.

---

### Post by Baelus on 2009-10-15
This may help:

[http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/]("http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/")

---

### Post by alphaniner on 2009-10-15
Have you looked at [this]("http://ubuntuforums.org/showthread.php?t=442945")?

---

### Post by oldfred on 2009-10-15
alphaniner link has lots of good info, and comments by Herman. But the links to Herman's site have moved to:

[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

His discussion on error 17 which is similair to Baelus link.
[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

If you need help figuring out what to change to fix this:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by kumaresan89 on 2009-10-16
> **Baelus said:**
> This may help:

[http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/]("http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/")

Thanks it worked..

---

