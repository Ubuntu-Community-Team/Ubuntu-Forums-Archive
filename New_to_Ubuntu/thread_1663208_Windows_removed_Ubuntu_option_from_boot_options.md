---
title: "Windows removed Ubuntu option from boot options"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by ankur.trapasiya on 2011-01-09
Hello 

due to some .NET work i had to install windows. Therefore i installed windows on my pc today without formatting my system. Now as i installed windows it removed boot time options for selecting Ubuntu as operating system. 

Now i want to log in into ubuntu. My important data resides there and i have to work with it also..

How can i boot in ubuntu now??.. It is not showing me options for booting in ubuntu ....

---

### Post by Verbeck on 2011-01-09
if you install windows after ubuntu, the windows boot loader would overwrite grub2 in the mbr.
see the following link on how to recover grub2 >>>
 [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

same thing as above, but cleaner>>>
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

hope that helps

---

