---
title: "&quot;smb:///&quot; is not a valid location."
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by satbunny on 2007-03-28
When I try to browse the my samba network (hosted on Ubuntu 6.06 Linux box VAIO) Nautilus returns the following error:

"smb:///" is not a valid location.

My other Linux box (Ubuntu 6.10 Dell) says the same.

My Win XP and Mac OSX boxes browse the samba shares happily.

I can mount samba shares using fstab on both Linux boxes.

I have read many posts here, some people have the same problem, but I couldn't find a clear solution:

Here it is: [http://e-volutiononline.com/blog/ubuntu-smb-error.html](http://e-volutiononline.com/blog/ubuntu-smb-error.html)

> The trick the worked was to install the package called libgnomevfs2-extra

I installed that and voila, problemo solved. If you get the &#8220;smb:/// is not a valid location&#8221; error then try this out and let me know if it fixes it for you.

You can install this package using the built in Package Manager or using the apt-get command at the command prompt.

---

