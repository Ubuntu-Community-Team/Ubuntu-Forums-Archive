---
title: "grub: boot failed! (Ubuntu 11.04 + Windows 7)"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by Nestar on 2011-04-17
Hello Ubuntu Community!

I just installed Ubuntu 11.04 (x64) Natty Narwhal along my Windows 7 OS. I've been using the new Ubuntu for a few days and today I wanted to reboot into Windows 7 to play some games.

The only thing I can see after selecting W7 on a totally black screen, though, is:

```
Boot failed!
```

Does anyone know how I can fix this problem? Reinstalling and reconfiguring grub didn't help so far.

Thanks in advance!

---

### Post by coffeecat on 2011-04-17
Hi, and welcome to the forum.

I've never seen a "Boot failed!" error message before. That's certainly succinct. It sounds like a Windows message rather than a grub message, but rather than speculate, let's do some investigation.

With boot problems, it's helpful to run the boot info script to get some idea of what might be wrong, as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Don't download the script from there though. If you do you'll get version 0.55 which is not compatible with Natty. To get version 0.56, open a terminal and run this command:

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
```

Move the boot script file to your desktop and now run:

```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

A file RESULTS.txt will appear on your desktop. Post the contents of that between [noparse]```
 and 
```[/noparse] tags for clarity.

Also - do you have a Windows 7 installation DVD (it has to be a Microsoft one - not an OEM manufacturer's) or a Windows 7 repair CD?

---

### Post by Leppie on 2011-04-17
what make is your machine?
you may have to restore to windows boot loader

---

