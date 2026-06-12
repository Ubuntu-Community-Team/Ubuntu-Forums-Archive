---
title: "No GRUB at boot, boots straight to Windows"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Redbeard09 on 2009-05-05
I installed 9.04 after installing the Windows 7 RC. Instead of showing the GRUB menu at boot with the option for Ubuntu and Vista Loader, it boots straight into 7. I followed the instructions here ([http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)) to manually reinstall GRUB but it has no effect. Any suggestions on how to get GRUB working?

---

### Post by Didius Falco on 2009-05-05
Hi,

Boot up with your Live CD and download this little (57k) script to your desktop:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)


Then open a terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh

```The script will gather a lot of information that will help figure out the problem into a file named CONTENTS.txt

Open that file, select all and paste it in this thread, then put code tags (the # on the toolbar) around it.

It'll help people figure out the problem faster...

Regards,

Didius

---

### Post by blueridgedog on 2009-05-05
I think you neglected to attach the script.

---

### Post by djbushido on 2009-05-05
True that.
Anyway, if you could also post "cat /boot/grub/grub.conf;cat /boot/grub/menu.lst" that would be great.

---

