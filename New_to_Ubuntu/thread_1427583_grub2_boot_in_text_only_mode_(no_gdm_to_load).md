---
title: "grub2: boot in text only mode (no gdm to load)"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by Den-den on 2010-03-11
Yes, I have googled and searched the forums for this, but no hope :'''(
I'm running 9.10 Karmic with the latest updates.

How can I boot into Ubuntu without automatically loading GDM?
Perfectly if I was able to choose the option in the grub menu list.

Is there a way I can do this?

---

### Post by Locke_99GS on 2010-03-11
Try adding *init=/bin/sh* as a kernel argument in an extra grub entry. (or add it on the fly with 'e' in grub.) This should skip the init scripts and take you straight to a shell.

---

### Post by Den-den on 2010-03-12
As this is Grub2, would it have to go to /etc/default/grub.d as a new script file?
Sorry, I'm so confused with grub2! Would you mind giving some'semi-idiot-proof' instructions please? Thank you!

---

### Post by tom4everitt on 2010-03-12
The easiest is probably to temporarily give yourself write-permission to grub.cfg and manually duplicate one of the entries there with the desired option appended. 

If it works you can just put the entry in /etc/grub.d/40_custom and it will automatically be appended to grub.cfg when update-grub is run.

---

### Post by Method X on 2010-03-12
why not to just delete grub?

---

### Post by dentex on 2011-01-30
> **tom4everitt said:**
> Try adding *init=/bin/sh* as a kernel argument in an extra grub entry

Hi, I came across this thread searching for the same topic on the net; somewhere else I found that the "rw" option gives also write permission on the file-system, that should be ok if you are going to fix something. 
But it has to be put before, like ```
linux /boot/vmlinuz-X.X.XX-XX-generic root=UUID=<STRING> rw init=/bin/bash 
```The strange thing (to me, at least; I'm not an expert) is that you're not able to logout, shutdown or reboot: "exit" or "CTRL+D" brings to *panic* and the other two simply hangs. I had to brutally press the power-button to shutdown the PC.

---

