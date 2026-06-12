---
title: "Xfce"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-09-02
Hi
This problem has reared it's ugly head again I uninstall something and ubuntu goes and Xfce appears
I entered the code below  log out but when I go for  Options > Select Session > Gnome > Change Session >
Gnome isn't there?
 
1. Reinstall the ubuntu desktop (replace this with kubuntu-desktop if required)
 	Code:
 	sudo aptitude reinstall ubuntu-desktop 
2. Log out, and choose your preferred desktop (Gnome, xfce, whatever)
3. When asked, click on the option to make your choice the default. 		                   		  		  		 		 			 				__________________

---

### Post by kerry_s on 2009-09-02
ubuntu-desktop is just a meta package, removing it does not do nothing.

sounds like you have already got a boned install, save what you want & start again.

---

### Post by Anybloodyid on 2009-09-03
I didn't remove it something I removed, is what removed it. Up till that point it was working fine.
Thinking of keeping XFCE now anyway as it doesn't crash like Ubuntu did.

---

### Post by nothingspecial on 2009-09-03
Removing evolution removes ubuntu-desktop, so does removing alsa-utils.

---

### Post by kansasnoob on 2009-09-03
Look at this section:

> Playing Around
KDE/Gnome Comparison
Install KDE
Install XFCE
Install IceWM
Pure Gnome
Pure KDE
Pure XFCE
Make your own Ubuntu remix

here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by mcduck on 2009-09-03
> **nothingspecial said:**
> Removing evolution removes ubuntu-desktop, so does removing alsa-utils.

Removing any program included in the default Ubuntu install removes "ubuntu-desktop". Which is just empty metapackage and doesn't actually remove anything else from your system. Removing ubuntu-desktop is absolutely fine, you only need to remember to reinstall it when upgrading to new Ubuntu versions.

Removing certain Evolution components, or alsa-utils removes *Gnome* itself.

---

### Post by nothingspecial on 2009-09-03
That`s what I meant

---

### Post by Anybloodyid on 2009-09-03
Thanks to all

---

