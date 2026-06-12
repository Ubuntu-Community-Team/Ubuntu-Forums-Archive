---
title: "Help please!"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by dansar on 2009-06-01
Help! I downloaded Ubuntu thru Wubi. How do I get to it? Only way I know I actually have it is thru my REVO uninstaller program but I cannot open it from there. Windows search does not find the file. Nothing shows in My Documents folders or All Programs.

---

### Post by starcannon on 2009-06-01
Are you attempting to Boot/Run Ubuntu, or Create an Ubuntu Install CD?

If your simply trying to Boot Ubuntu, then restart your machine; you should see a text message during the boot up process asking you what Operating System you would like to use for this session, Ubuntu or Windows. Choose Ubuntu, if all went as planned you should end up at a Gnome Desktop.

If you are trying to locate the Ubuntu ISO that Wubi used to install Ubuntu, just search for ```
*.iso
``` Unless you have a vast and extensive .iso collection, this search should give up where on your computer your Ubuntu CD Image is located.

GL

---

### Post by dansar on 2009-06-01
I didn't receive any message as to a boot choice as far as I remember. It booted right into XP. I know where the Wubi installer file is. I already did that. I just want to boot into Ubuntu. I'll try to reboot again. thank you for the reply. Dan

---

### Post by dansar on 2009-06-01
ok..I rebooted and the first screen that came up was black with a small white line in the upper left corner then proceeded to boot into XP. There was no text message.I know I have Ubuntu because the 8 gig's I alloted for it are missing from my C partition.

---

### Post by starcannon on 2009-06-01
> **dansar said:**
> ok..I rebooted and the first screen that came up was black with a small white line in the upper left corner then proceeded to boot into XP. There was no text message.I know I have Ubuntu because the 8 gig's I alloted for it are missing from my C partition.

Press ESC when you get the black screen with the white line; that "should" bring up a boot menu if memory is serving me correctly (I haven't played with Wubi in a long time)

---

### Post by starcannon on 2009-06-01
Be sure to check out these nice tutorials:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by BlazeFire247 on 2009-06-01
There's supposed to be a menu that allows you to select whether you want to use Windows or Ubuntu when you use Wubi to install it.

---

### Post by dansar on 2009-06-01
Well..I pressed ESC but it still booted windows.  I tried pressing F8 but there was no Ubuntu option. Now I'm wondering if I uninstall Ubuntu will I get my 8 gigs back to C.  I'm glad I'm trying this on my old HP. LOL  The install went as easy as they said it would. I dont understand why I can't boot into it. Must be a way. Thank you for your replies. Dan

---

### Post by starcannon on 2009-06-01
After you uninstall it, you may need to delete the folders it created on your hard disk to get the 8gigs back. [https://wiki.ubuntu.com/WubiGuide#How do I uninstall Wubi?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20uninstall%20Wubi?") Be sure to back up the iso file so that if you want to experiment again or on another machine, you won't have to re-download the disk image again.

GL and have fun.

---

### Post by dansar on 2009-06-01
Hey.. Thanks guys.  I read the tutorial you posted and found the answer. control panel>system>advanced>startup/recovery then checked the box..time to show operating system option. LOL..something like that.  Thanks again. Dan

---

