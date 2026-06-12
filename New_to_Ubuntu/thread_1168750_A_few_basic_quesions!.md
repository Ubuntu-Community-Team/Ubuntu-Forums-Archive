---
title: "A few basic quesions!"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by hellothere2 on 2009-05-24
I would like to install ubuntu on a computer that currently uses windows xp.  However, this computer is not only used by me.  Because of this, I need to install it in a way such that windows xp can still easily be run.  I'm not just saying that I don't want to lose  the files; I acutally want to still be able to use xp on the computer (exactly how it currently is).  Is this possible?  If so, how do I go about doing this?

Also, just in case this doesn't work out, is it easy to uninstall ubuntu? 

Thanks!

---

### Post by jimmy the saint on 2009-05-24
Here is the Documentation for accomplishing that.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by skyjacker on 2009-05-24
> **hellothere2 said:**
> I would like to install ubuntu on a computer that currently uses windows xp.  However, this computer is not only used by me.  Because of this, I need to install it in a way such that windows xp can still easily be run.  I'm not just saying that I don't want to lose  the files; I acutally want to still be able to use xp on the computer (exactly how it currently is).  Is this possible?  If so, how do I go about doing this?

Also, just in case this doesn't work out, is it easy to uninstall ubuntu? 

Thanks!
You can set up partitions on the hard drive and "dual boot" your system. This will allow you to start either Ubuntu, or Xp each time to restart the PC. 
See this link for more help...[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by snowpine on 2009-05-24
Check out Wubi. It installs Ubuntu like a windows application. It is the safest way to try Ubuntu without any risk to your windows install.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by hellothere2 on 2009-05-24
Thanks to all!  

But what about uninstalling ubuntu?  Is this easy to do?

---

### Post by jango102 on 2009-05-24
Not quite as easy as installing it, no. You'll have to get rid of the partition on your hard drive that holds Ubuntu, and you'll have to tell your computer to start booting using Windows instead of trying to boot using Ubuntu's loader. This is explained in much more detail here: [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)
If you plan on uninstalling ubuntu, make sure you have the Windows XP install disc that came with your computer when you bought it.

---

### Post by RJ12 on 2009-05-24
I use Wubi and if you want to uninstall it just go to Add/Remove Programs in XP then click Ubuntu and uninstall I have the exact same thing.

---

### Post by ugm6hr on 2009-05-24
> **hellothere2 said:**
> Thanks to all!  

But what about uninstalling ubuntu?  Is this easy to do?

If you use Wubi, it allows you to uninstall just as you would any other program.  The risk to your files is similar to installing any other application.

Wubi gives you a reasonable feel for Ubuntu, but is not quite the same as a proper "dual-boot" situation.

A proper dual-boot is more difficult to uninstall, but gives you a more complete Ubuntu experience.  If you go down this route, ensure you have backed up your personal files, since repartitioning can cause corruption.

---

