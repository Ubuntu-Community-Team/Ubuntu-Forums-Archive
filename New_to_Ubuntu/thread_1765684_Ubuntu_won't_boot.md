---
title: "Ubuntu won't boot"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by Bunnies on 2011-05-23
> mount: mounting /dev/disc/by- uuid/44cd5909-6b4a-4780-8bc0-cdc 3267 beb63 on /root

Failed: invalid argument
Mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed no such files or directory
mount: mounting /proc on /root/proc failed: no such file or directory
target file system doesn't have /sbin/init.
no init found. try passing init=bootorg.

Busy u1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


I keep getting this error whilst trying to start up Ubuntu. I've done nothing to warrant this error that I'm aware and looking for a fix - any recommendations?

Thanks

---

### Post by Bunnies on 2011-05-23
I hate to bump this, but I really do need a fix >.<

Any ideas, anyone?

---

### Post by fidamehran on 2011-05-23
> **Bunnies said:**
> I hate to bump this, but I really do need a fix >.<

Any ideas, anyone?

I'm not quite sure. But I think I saw this problem somewhere before. The problem was stated to be inappropriate installation from an inappropriate installation disk/source.

Try checking the md5 of the Ubuntu ISO download, then run it or burn it again with a strong CD writer.

Then reinstall.

---

### Post by Bunnies on 2011-05-23
The version of ubuntu was working properly for a long time after the installaiton with no additional errors.:confused:

---

### Post by Mark Phelps on 2011-05-24
Is this an Ubuntu only PC? Or are their other OSs on this PC as well?

Have you tried getting into the GRUB menu and choosing the Recovery Mode option?  If you're not getting a menu, try holding down the SHIFT key while booting.

---

