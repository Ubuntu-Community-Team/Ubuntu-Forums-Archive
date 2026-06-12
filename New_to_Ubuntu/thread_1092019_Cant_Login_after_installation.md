---
title: "Cant Login after installation"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Binny88 on 2009-03-09
Hi

My friend Installed Ubuntu 8.10 on his machine. It is a Pc with 512 MB ram and Intel chipset and onboard graphics. He assigned about 6GB for Ubuntu and 500 for swap. After restarting post Installation he typed his username and pasword and he was greeted with a brownscreen minus the icons.Only the mouse is present.I cant understand what happened?

Solution anyone?

Thanks

---

### Post by finer recliner on 2009-03-10
try booting into safe mode. then run the Xorg reconfigure script (the exact command is located in the comments of /etc/X11/xorg.conf). reboot, and see if that fixed anything.

---

### Post by Binny88 on 2009-03-10
Thanks for the advice, Can you please tell me the command to stop the xserver.

Thanks again

---

