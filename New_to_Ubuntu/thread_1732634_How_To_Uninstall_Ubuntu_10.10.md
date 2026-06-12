---
title: "How To Uninstall Ubuntu 10.10"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by chelski4life on 2011-04-18
Hello, 

I found i dont use ubuntu enough and it seems to have actually effected me ability to webchat someone, anyway, i wish to delete the Ubuntu parition which are logical on my hard drive and not add it back to my win7 partition but have it as a partition seperartly that i can store files on, as i do not have a Win7 disk my PC did not come with one when i bought so i cant do a system recovery, would it be possible to delete all my ubuntu partitions then just make a new one that is a NTFS ?

Can some people tell me how and if it is possible :) THANK YOU sorry for leaving he ubuntu community i tried my best but its obv not suited for me :(

---

### Post by gyyug78fg87ogguiioioioioi on 2011-04-18
[http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

---

### Post by chelski4life on 2011-04-18
> **gyyug78fg87ogguiioioioioi said:**
> [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

I dont have the disk or anything thou this is my problem :(

---

### Post by Miljet on 2011-04-18
It is a simple matter to boot from a Ubuntu Live CD, use Gparted to reformat the existing Ubuntu partition to NTFS. Your problem is going to be replacing GRUB in the hard disk MBR (Master Boot Record) without a Windows install CD.

You might want to try this:
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Or I believe that you can download something from Microsoft that will repair the MBR.

At any rate, make sure that the MBR points to the correct Windows boot loader BEFORE removing Ubuntu. Otherwise you won't be able to boot your computer at all.

---

### Post by chelski4life on 2011-04-18
> **Miljet said:**
> It is a simple matter to boot from a Ubuntu Live CD, use Gparted to reformat the existing Ubuntu partition to NTFS. Your problem is going to be replacing GRUB in the hard disk MBR (Master Boot Record) without a Windows install CD.

You might want to try this:
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Or I believe that you can download something from Microsoft that will repair the MBR.

At any rate, make sure that the MBR points to the correct Windows boot loader BEFORE removing Ubuntu. Otherwise you won't be able to boot your computer at all.

So once i have fixed that can i remove the linux partitions and it will all be safe ?

---

