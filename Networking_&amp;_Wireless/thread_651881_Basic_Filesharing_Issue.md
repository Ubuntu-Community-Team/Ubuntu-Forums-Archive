---
title: "Basic Filesharing Issue"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by helixed on 2007-12-28
Hey everybody,

I'm sure this is a simple question to answer but I've been trying to find an answer to it for a while now and I'm starting to get frustrated.  I have two Ubuntu 7.10 PC's, one which I would like to have run as a machine on which I can backup my files and perform various other tasks.  I've already got a VNC server running, but the file sharing is giving me a headache.  Here's what I've done:

On the server PC (it's not running the server edition of Ubuntu, just to clarify), I went into Shared Folders under Administration and told it to install both NFS and SMB (I doubt I'll be connecting a windows PC, but you never know and I thought it might come in handy some day).  I told it to share a folder I created in my home directory.  As the allowed host, I put in the IP address of my client computer.  When I first installed the NFS network items, I could see the server computer under the Network tab in the Places tab, but now it's not there at all.  

Can somebody please tell me what I'm doing wrong?

Thanks,

Helixed

---

### Post by icheyne on 2007-12-28
I have never had luck file sharing using the GUI tools. The command line does work fine though.

[http://planetmayhem.org/easy-peasy-ubuntu-linux-nfs-file-sharing](http://planetmayhem.org/easy-peasy-ubuntu-linux-nfs-file-sharing)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by paul.matthijsse on 2007-12-28
Hello, I do that trick with ssh, I installed the following on two Ubuntu 7.10 machines:
$ sudo apt-get install openssh-server ssh

Now you can connect to the other machine in various ways (gui or cli). Hope this helps.

Cheers, Paul.

---

### Post by helixed on 2007-12-28
icheyne, your second guide worked perfectly.  I think my problem was I wasn't mounting the shared folder.  Anyway, thanks again for the help.

Helixed

---

