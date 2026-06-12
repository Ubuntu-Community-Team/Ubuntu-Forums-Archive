---
title: "Linux to Linux Networking"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by delphiguy on 2007-11-04
Cheers,

My current setup is that my main workstation is Ubuntu, and I have setup Samba so that my
Vista Laptop (yeah I know, but I have no choice), could see my shared resources.

And now I am resurrecting my old P3 600mhz machine, and I am going to install xubuntu in it.
And I am now going to make it my server sort of (ftp, torrents, etc.), so I need to have my three systems
to be able to transfer files between them.

Can anyone point me in the right direction?

Thanks.

---

### Post by TheOctagon on 2007-11-04
--deleted--

---

### Post by vinnn on 2007-11-04
Quick Answer: NFS or SSH, your choice.

---

### Post by delphiguy on 2007-11-04
hi vinn, could you elaborate further, i am a newbie in linux, im sorry.

---

### Post by delphiguy on 2007-11-04
thanks vinn for the help, I googled Ubuntu+NFS, and I got a few howto's.
now i just have to wait for xubuntu to finish downloading and i'll be working on it.

thanks.

---

### Post by vinnn on 2007-11-04
Well firstly, setting up some basic NFS & Samba shares is really easy to setup in Xubuntu, just goto [Applications] > [System] > [Shared Folders].
In Ubuntu the same tool is at [System] > [Administration] > [Shared Folders].
This tool makes it easy for you to install NFS server & Samba server and configure each. You'll have your files shared out in no time.

Having just re-read your first post it sounds as if you'll be using the Xubuntu box to share files out to both Linux & Windows PCs.
I'd setup an NFS share (proper name 'export') to serve out to the Linux PC/s. As Windows does not include an NFS client, configure Samba to share files out to the Windows PC/s.

---

### Post by delphiguy on 2007-11-04
Thanks for the help vinnn, still downloading xubuntu at the moment.
gonna work on it as soon as the download finishes.

---

