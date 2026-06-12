---
title: "Installation problem with Sony Vaio VPCCW1S1E"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by sombathely on 2010-12-12
Hi everyone!

I have a Sony Vaio Laptop with Windows 7 and discovered the Windows Installer on the Ubuntu website. I just wanted to try out Ubuntu and thought this installation method would be a good way to do it.
I used the wubi program to download and install ubuntu 10.10 desktop version.
I then rebooted and on the screen I could choose whether to book Windows 7 or ubuntu.

I chose ubuntu and then after a few lines of text, the screen went (totally) black (as if switched off). And then nothing happens any more.

I've tried rebooting several times -- doesn't work.
Since I was told that ubuntu is very easy to install and work with I was a bit surprised -- why does this happen? Sony Vaios are very common, why would there be an incompatibility?

---

### Post by Hippytaff on 2010-12-12
Welcome to the forums :-)

Do you know what graphics card you have? is it Nvidia?

---

### Post by sombathely on 2010-12-12
My graphics card is Nvidia GeForce GT 230M



> **Hippytaff said:**
> Welcome to the forums :-)

Do you know what graphics card you have? is it Nvidia?

---

### Post by Hippytaff on 2010-12-12
When you get to the bit in the boot process where you get to choose which os to use highlight ubuntu and press e. Delete quiet splash and type nomodeset in it's place, then boot. When you get into ubuntu go to system -> Administration -> alternate drivers and install the suggested Nvidia driver :-)

---

### Post by sombathely on 2010-12-13
Thank you, [Hippytaff]("http://ubuntuforums.org/member.php?u=1133249"), that was very helpful!!
I could boot ubuntu for the first time and everything worked well.

However, after installing the recommended Nvidia driver and rebooting, the same problem happened (black screen)...

So I uninstalled it again and now it's working again. The screen resolution seems fine for me. Since I don't really need the 3D support for this system, I think I can live with the current configuration (with the proprietary Nvidia driver).

But: whenever I boot ubuntu now, I always have to replace the "quiet splash" with "nomodeset" manually before booting. Otherwise the black screen reappears.
Is there any way I can specify in the settings that ubuntu automatically starts up with theese default settings that work?

---

### Post by Hippytaff on 2010-12-13
You need to edit, as root, the file /etc/default/grub.
 
to edit as root do ```
 gksudo /etc/default/grub
```. and replace the line with quiet splash with nomodeset, then save.

---

### Post by sombathely on 2010-12-13
Thanks!
I think I'm all set now, it worked.

But I had to use "sudo gedit /etc/default/grub" on my system and then do an update with "update-grub".

---

### Post by Hippytaff on 2010-12-13
Oh yeah, forgot about the update-grub bit. If you're happy that the issue is resolved please mark the thread as solved in the thread tools at the top of the page :-)

---

