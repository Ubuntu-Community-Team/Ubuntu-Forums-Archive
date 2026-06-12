---
title: "Need help:  Setting up a discless network"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by mrbarky on 2007-12-27
For school I'm doing a networking project where we have to setup a discless network using a server and 2 end clients.  About all we have done so far is installed ubuntu on the server and acquired the 2 discless end clients.  We are really not sure what to do next to set them up so I was wondering if anyone could help out with any tutorials of how to do this and if there's any other software we will need, what it will be?  Thanks so much in advance.

---

### Post by gilf on 2007-12-27
What is meant by discless? HD-less? CD-less? USB thumb drive-less? floppy-less?

How did you set up your server without a disk of any sort, unless it also is on a network with a file server?

---

### Post by mrbarky on 2007-12-28
Discless meaning no hard drive.  We installed ubuntu onto the server using a CD, it's just the end clients that don't have a hard drive nor a CD drive.

---

### Post by mips on 2007-12-28
[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
[http://pachikov.com/ablog/posts/2006/03/07/terminal-server-for-home-media-pcs/](http://pachikov.com/ablog/posts/2006/03/07/terminal-server-for-home-media-pcs/)
[http://www.playingwithwire.com/2007/08/building-a-modern-it-infrastructure-for-a-small-company-10-clients-with-a-sub-3000-budget/](http://www.playingwithwire.com/2007/08/building-a-modern-it-infrastructure-for-a-small-company-10-clients-with-a-sub-3000-budget/)

You will have to boot over the network with PXE.

I suggest your look at Edubuntu as it has LTSP preinstalled.

---

