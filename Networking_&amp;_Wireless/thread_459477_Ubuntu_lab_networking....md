---
title: "Ubuntu lab networking..."
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by hungrysam on 2007-05-30
I have an ubuntu lab with 9 edubuntu computers and one ubuntu server.  The *buntu computers are able to see the WinXP, Vista, etc.. computers on the network, but they can't see each other.  Also, when I went to install my local printer, my Ubuntu found 2 other printers that are connected to 2 Vista machine on my network.  Is there any way to use those?

---

### Post by spd106 on 2007-05-30
Have you read through the Edubuntu Cookbook? There's loads of information in there.
[https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/](https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/)

As far as I know each of the PCs have a samba client, but no server installed by default. If you want to have them sharing files you will need to install a samba server on each them. This is not always recommended, it depends on what you want to achieve as there are other methods. 

Often it is better to host all files on the main server. That way you have a central file store that can be backed up easily. There is also the greater central control and flexibility than in a peer to peer model.

---

