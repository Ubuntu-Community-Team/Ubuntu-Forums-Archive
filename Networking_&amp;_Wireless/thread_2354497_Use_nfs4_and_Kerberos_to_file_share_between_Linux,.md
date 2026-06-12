---
title: "Use nfs4 and Kerberos to file share between Linux, Windows, Andriod and IOS?"
date: 2017-03-03
forum: Networking &amp; Wireless
---

### Post by sunbear-c22 on 2017-03-03
Scenario: Network has a router connected to modem. Router is also connected to 2 Ubuntu 16.04 computers and Window computers and Android & IOS mobiles via LAN and WiFI.

1. Is it possible to use nfs4 to file share between all these devices. If yes, how?
2. Is Kerberos security appropriate only for networking Linux based systems or can it also be applied to the other systems?

---

### Post by TheFu on 2017-03-03
The short answer is no.

The longer answer is, perhaps.  Just because something can be done, doesn't mean you should.  NFS demands a solid network connection. People using wifi for RW connections are asking for data corruption. For read-only - fine. Just not read-write.

I don't know of any NFS clients for iOS or Android. Definitely aren't any NFS servers.  The Windows NFS stuff hasn't worked for me in over a decade. I think a commercial solution is necessary ($100+), not the client included in Windows Enterprise and above.

So, you'll want to decide which systems have to be storage servers and which can only be storage clients.

I have used read-only NFS mounts over the internet from 2K miles away, but that wasn't for anything sensitive and no authentication was necessary. It was a glorified FTP server for access by anyone in the world.

The best way I know to share files with iOS and Android is via SFTP.  There are sftp clients for every OS with a network stack that I know. Streaming media over SFTP isn't usually supported.  Just depends on the type of access desired.

You might want to look into **NextCloud**, if you want to take the files with you while disconnected.  However, be very cautious using tools like this over the internet without a full VPN. I don't trust HTTPS, BTW. Everyone needs to decide on their own security needs, however. 

Also, I would decide on 1 system of record and have only that system do the sharing. Much easier to secure 1 box than 5+.

---

### Post by sunbear-c22 on 2017-03-04
@TheFu Thanks for your advises. 

Concerning the data corruption that you had mentioned for people using wifi rw connection, does that also apply to folks sharing files between linux machines also, or just apply to between windows and linux file sharing. 

It's a pity.

---

### Post by SeijiSensei on 2017-03-04
I'll just say that I have used NFS over wifi connections for years without incident, but only between computers.  Neverthless I don't think NFS will solve your problems because of a lack of clients for mobiles, never mind including Kerberos support.  (Not to mention that the Windows NFS client [only comes with Win 10 Pro and Win 10 and Win 7 Enterprise and Ultimate versions]("https://forums.freenas.org/index.php?threads/how-to-connect-to-nfs-share-from-windows-10.44412/#post-297748").)  You can use CIFS, the standard method of file sharing in Windows, with Samba on Linux, and clients like AndSMB for Android. Not much in the way of security with vanilla CIFS though. 

It sounds like you're just trying to share files within a home or small office situation, no?  I have a centralized Linux file server that runs servers for Samba and NFS.  Linux clients use NFS; Windows clients use CIFS.  It's rare that I need a file from the server on my phone except for media.  There I use minidlna on the Linux box with the stored media.  If I do need a file, I can use AndSMB on my Android devices.

Some of my machines are connected by wires; some by wifi.

If you have an Active Directory network with Kerberos already, then I'd look into [methods to integrate Linux machines with AD]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto").

---

