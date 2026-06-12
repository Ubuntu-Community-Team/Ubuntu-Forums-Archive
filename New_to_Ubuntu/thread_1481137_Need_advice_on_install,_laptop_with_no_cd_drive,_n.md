---
title: "Need advice on install, laptop with no cd drive, no working usb ports"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by philodice on 2010-05-12
Can ubuntu be installed by downloading it directly from the internet?  So far this is the only way I've found to get anything onto this computer.

The cd drive isn't working, it has no 'boot from usb' in bios, and is running windows 2000.  Laptop is about 7 years old.

---

### Post by Paddy Landau on 2010-05-12
The only way that I know of is to install Ubuntu as a program within Windows.

For this, you use [Wubi]("http://wubi-installer.org/"); it installs and uninstalls as a normal Windows program. To run Ubuntu, you need to reboot; to go back to Windows, you need to reboot again.

Wubi has its caveats (read the [Wubi FAQ]("http://wubi-installer.org/faq.php")).

You need to be aware that when install Wubi, there is a tiny chance of catastrophic failure, rendering your Windows unbootable. If that happens, without a CD drive or bootable USB port, you'll be screwed. You'd need to install a new CD drive, and that will probably cost you the same as getting a Linux netbook anyway.

So, back up your data first!

Of course, with such an old machine, you might not have the space to install Wubi. Were you intending on getting rid of your Windows and replacing it with Ubuntu, or having both systems on your machine?

---

### Post by skyeric on 2010-05-12
is the CD drive definetly completely useless? does windows recognise it and it just not work or what? installing new CD drive drivers could be worth a try if you haven't already.

if not wubi is the only option i know off yes so go with the advice above.

---

