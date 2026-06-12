---
title: "How do I grant access to a specific directory to a specific IP address?"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by guitarplaya85 on 2008-10-09
My girlfriend and I wish to share our music folders with one another.  We live in different towns, so we would need to do this over the internet.  How can I grant her IP access to my music folder without granting access to the rest of the computer and without leaving it open to other IPs?

---

### Post by handydan918 on 2008-10-09
> **guitarplaya85 said:**
> My girlfriend and I wish to share our music folders with one another.  We live in different towns, so we would need to do this over the internet.  How can I grant her IP access to my music folder without granting access to the rest of the computer and without leaving it open to other IPs?

I am unaware of a way to do this. However, it should be trivial to grant your GF an account on your local machine, and give her permission to access the folder. You could even specify read only or read-write. Then you would have to determine the best way to connect...remote desktop perhaps?

---

### Post by Iowan on 2008-10-09
[VPN]("https://help.ubuntu.com/community/SSH_VPN") might keep other computers at bay, but I'm not sure about limiting access.  Dunno if [SSHFS]("https://help.ubuntu.com/community/SSHFS") would work via VPN, or if it could limit access.

---

### Post by doas777 on 2008-10-09
a vpn is defn the way to go. your folder sharing would not likely work over the internet, though it you could you could use a firewall to restrict traffic incomming on your sharing protocol port to the remote IP.

a vpn is a much better plan. vpns extend your local network physically so your remote pc acts as thought it were in the next room (except much slower). it's also encrypted so you don't have to worry about passing media files through devices that are monitoring for specific file hashes. or you could set up SSH and use scp to transfer files. thats pretty easy.

good luck,
Franklin

---

### Post by ProgramErgoSum on 2008-10-10
Since it is the folders you want to share, suppose you ran a tiny FTP server on your machine, gave your GF an id/password and limit access to that folder, it might work out. For example, [gFTP]("http://gftp.seul.org/")

SSHFS is also a nice idea.

BTW, is limitation to an IP address really viable ? I mean, what if your GF is on Wireless and connects/disconnects at various places ? Or, what if the GF's laptop is rebooted and static IP is not applied ?

---

### Post by guitarplaya85 on 2008-10-14
Thanks all!  Completely noob question I guess.  I ended up setting up a small FTP.

---

