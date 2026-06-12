---
title: "exaile and songs on secondary drive"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by TehDuke on 2009-04-12
hey guys,

I'm having a strange problem with the secondary ssd card (8gb) in my eee pc 901.

I put some music on the 8gb card and I started using exaile and linked it to the music on that card. But now i have the problem that when I reboot my computer, exaile can't see all my songs unless I first open the 8gb card with the file browser.

Is there a way i can get exaile to work without having to do that every time? Is it something to do with mounting?

I am quite new to Linux so forgive me if this is a stupid question.

Thanks in advance...

---

### Post by SathyaBhat on 2009-04-12
Indeed, the SSD has to be mounted. Use a tool like pysdm to add an entry to /etc/fstab to automount the drive. (ref: [http://sathyasays.com/2008/10/08/how-to-automount-hard-drive-partitions-everytime-you-login-in-linux/](http://sathyasays.com/2008/10/08/how-to-automount-hard-drive-partitions-everytime-you-login-in-linux/) )

---

