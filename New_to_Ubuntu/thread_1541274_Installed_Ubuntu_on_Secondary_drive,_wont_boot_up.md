---
title: "Installed Ubuntu on Secondary drive, wont boot up"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by Malik on 2010-07-28
I installed ubuntu on a secondary drive but it just boots up windows xp when i restart.

I then tried installing ubuntu on the primary drive but it wouldnt let me without erasing it entirely.

How do I install ubuntu on the secondary drive and let it ask me which OS I want?

Thank You.

edit: [IMG]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step4b.png[/IMG]

I dont get that picture when trying to install on main drive.

---

### Post by k3lt01 on 2010-07-29
GRUB should install on the main drive. If it didn't the main drive will continue to use NTLDR (NT Loader) the Windows native boot loader and it wont see your Ubuntu drive.

---

### Post by jtarin on 2010-07-29
If your running Vista or Win7 you can use [EasyBcd]("http://neosmart.net/forums/showthread.php?t=642") to boot all you OS's, using The Win Loader.If Grub is on the MBR of your secondary drive...leave it there.Get the 2.0 latest build...they are all stable...just moreso.

---

### Post by gallifrey on 2010-07-29
Alternatively, if you have Ubuntu on your second drive still, either find out whcih key lets you access the boot devices when you startup. or change boot device in your bios whenever you want to use Ubuntu. 

Of course, this is less efficient than previous suggestions, but is a temporary workaround. 

If you intend to use Ubuntu regularly, you need to install Grub/Grub2 to your first hard drive MBR, usually sda or hda.

---

