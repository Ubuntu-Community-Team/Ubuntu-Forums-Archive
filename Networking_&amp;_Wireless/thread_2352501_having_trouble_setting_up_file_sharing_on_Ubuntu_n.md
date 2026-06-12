---
title: "having trouble setting up file sharing on Ubuntu network"
date: 2017-02-13
forum: Networking &amp; Wireless
---

### Post by jon114 on 2017-02-13
I know this has probably been asked a thousand times but I'm not finding anything helpful when searching so going to ask for myself.
I have a couple of ubuntu laptops running 16.04 and 14.04 and a desktop I want to use as a server also running 16.04 but can't get anywhere with file sharing.
I have followed the various threads on clicking on and creating a local network share but to no avail, nothing seen from the other pc's.
I have also tried to connect to server by typing in the ip of the desktop but it comes back as unanswered.
I tried to check up on samba (do I need samba or is that for a mixed linux-windows network?) but can't get any info from a status query as terminal comes back with service is masked or service is inactive/dead. Removed and reinstalled samba and the same result.
Some help would be very much appreciated.
Thanks
Jon

---

### Post by howefield on 2017-02-13
For your all linux network I'd suggest sshfs.

Although this page is not 100% correct it might give you an idea of what it is all about : [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by jon114 on 2017-02-13
Thanks howe, are there advantages to this method over the native file sharing system?

Does anyone have any advice on how to get the native file sharing working please? I've read quite a few threads on here which seem either massively complicated or don't work.

---

### Post by SeijiSensei on 2017-02-13
The standard for file-sharing on all *nix networks is NFS.  Samba was designed for Windows.  Here's a quick introduction to using NFS:  [https://help.ubuntu.com/14.04/serverguide/network-file-system.html](https://help.ubuntu.com/14.04/serverguide/network-file-system.html)

Make sure all the machines have the same usernames with the same associated user IDs.  Look at the file /etc/passwd on each machine to make sure.

---

### Post by jon114 on 2017-02-13
Thanks sensei but sorry I just don't follow that, not comfortable with the terminal as simply don't know what I'm typing.
Can you/someone not guide me on how to get the system that is already on my PC's working instead of installing something else?
I see other people posting about fine tuning and making adjustments to file sharing so it must be working for some?

---

### Post by jon114 on 2017-02-15
Bump, anyone successfully using the built in file sharing?

---

