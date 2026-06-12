---
title: "Peculiar(?) disk usage"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by SwatKat on 2009-11-07
Hi
I installed Ubuntu through wubi . I don't remember the exact installation size, but it was definitely not more than 8GB. I have been download happy, and have run out of disk space. I ran the disk usage analyzer and what it shows(screenshot 1) has me puzzled. If I am not mistaken , the size of the root directory is 12.2 Gb and the used space is 13GB. But I am sure that the installation size was not more than 8GB. Now, every time I boot into Ubuntu, I get the message in screenshot 2.  Could someone explain this to me please? I understand that the virtual disk can be resized using LVPM, but I want to know why I am getting the low disk space message* now*, and not when I exceeded 8 GB.

---

### Post by Paqman on 2009-11-07
Your total usage is 12.2GB out of 21.1GB. Of that Windows (showing as /host) is taking up 7.9GB. It looks like you might have only created a ~4GB virtual partition using Wubi. I'd suggest expanding it using LVPM, like you say.

In the meantime, some things you can do to free up space:
[LIST]
[*](Obviously) empty your trash
[*]Uninstall any unused kernels, they're over 100MB each. Search for "linux-image" in Synaptic and remove all except the one you're using.
[*]sudo apt-get autoclean && sudo apt-get autoremove. This will dump the package manager's cache and uninstall any obsolete packages.
[/LIST]

---

### Post by SwatKat on 2009-11-07
So thats what it shows. sudo apt-get autoclean && sudo apt-get autoremove cleared up a lot of space. Thanks.

---

