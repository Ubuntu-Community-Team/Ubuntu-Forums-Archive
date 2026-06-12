---
title: "Where is my grub file"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by pemilway on 2010-06-01
I have just started using Ubuntu.  Wanted to edit my grub file to change the default boot to Windows and found instructions online. When I try to run [FONT=monospace] [FONT=Verdana]"sudo gedit /boot/grub/menu.lst" I just get an empty file.

I have searched for a different location for my grub file but without success.

Thanks for any help you are able to give.



[/FONT][/FONT]

---

### Post by TeoBigusGeekus on 2010-06-01
It's an empty file cause you're probably using [grub2]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by bcbc on 2010-06-01
I like this [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

---

### Post by oldfred on 2010-06-01
If all you want is to have windows boot.

Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

---

