---
title: "How to remove Ubuntu dual-boot with Vista and just go back to Vista"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Haloman800 on 2010-10-13
Hello, I am running a Dell XPS m1330 computer with Vista OS and Ubuntu installed as an application, so on startup I choose between Vista and Ubuntu.
 
I tried Ubuntu, and it's just not for me.
 
My question now is, how do I remove Ubuntu entirely and just go back to Vista on startup?
 
I installed Ubuntu 10.04 with the disk they sent me.
 
 
Please give me detailed instructions, I found other posts on Google, but I don't entirely understand them.
 
 
Thank you very much.

---

### Post by AndyM3 on 2010-10-13
Installed "as an application"? Well then it's not a dual-boot, it's a Wubi install. Just find Ubuntu in Windows' "Add/Remove Programs", "Programs and Features" or whatever it's called now and uninstall it.

If you didn't install it *from windows*, things get more complicated. The easiest way is just to do a clean install of Windows, the hard way is to delete the Ubuntu partition using a LiveCD and "regenerate" the Windows bootloader using Windows' recovery/install disk. As far as I know, that is.

So, did you install it from Windows or by starting your computer from the CD?

---

### Post by coffeecat on 2010-10-13
> **AndyM3 said:**
> So, did you install it from Windows or by starting your computer from the CD?

@Haloman800, it's important to answer this question before you do anything, but to help, if you made a Wubi install, the installation process would have gone like this:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

On the other hand, if you did a conventional install with Ubuntu on its own partition, you need to repair the Windows bootloader on the mbr. The usual way is to use a Microsoft Windows install disc, or a recovery disc if you have one, but if you don't you can repair the Windows mbr using an Ubuntu live CD. You boot up with the Ubuntu live CD, make sure you have internet connected, open a terminal and do these commands:

```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```But don't do this until we're sure which type of Ubuntu installation you have.

---

