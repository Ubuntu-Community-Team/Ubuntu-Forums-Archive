---
title: "[SOLVED] not able to copy folder from network disk (files are ok)"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by sambody on 2008-07-04
Hi,

I'm using a LaCie Ethernet Disk Mini, which is a network disk attached to my router. I have copied/backed up files from an Apple MacBook Pro onto it, and now I am trying to copy those files from the network disk to my Linux machine, by using Nautilus.

The problem: single files copy just fine, but when I try to copy a folder, I get the following error:

```
Error while copying "foldername".
File unavailable

```

Can anyone help ?
Thanks.

---

### Post by superprash2003 on 2008-07-05
try this.. go to the terminal and type sudo nautilus.. a nautilus window should now open, now browse to the network disk and try copying with this window

---

### Post by sambody on 2008-07-05
> **superprash2003 said:**
> try this.. go to the terminal and type sudo nautilus.. a nautilus window should now open, now browse to the network disk and try copying with this window

I have opened nautilus like you said, but then I can't even access my network drive. As a normal user, in the nautilus side bar, I click on "Network servers" where I find "EDmini FTP", my network drive. But using sudo, when clicking on "Network servers", I get the following error message:

[HTML]Could't display network:///
Nautilus cannot handle network: locations[/HTML]

Is there another way to access my network drive ?

Thanks.

---

### Post by sambody on 2008-07-05
I have also tried to copy "ftp://192.168.2.5" from my location bar (when being in the drive folder) into sudo's location bar (in nautilus), but then I get the message:

[HTML]could't find "/home/sam/ftp:/192.168.2.5"
please check the spelling and try again[/HTML]

---

### Post by DuncanNZ on 2008-07-14
This looks like your problem here: [https://bugs.edge.launchpad.net/ubuntu/+source/gvfs/+bug/205370](https://bugs.edge.launchpad.net/ubuntu/+source/gvfs/+bug/205370)

---

### Post by sambody on 2008-08-04
I have updated my system and it seems the bug is now fixed. Thanks.

---

