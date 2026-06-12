---
title: "Auto Discovery of Samba Shares"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by drpepper on 2007-03-11
Hi everyone

I'm currently putting a mythbuntu box(mythtv + ubuntu) together and its going really well, i'm gonna document everything in a HOWTO on here at some point! anyway, what i need is ubuntu to auto-discover samba shares on the network and auto mount them. Then the user can share there music/videos across the network and play them on their mythbuntu box. The mythbuntu box is set-up to require aslittle as possible configuration from the end user, hence the need to auto discover and mount. Obviously the shares it finds will need no password and probably read only, but thats up to the user to setup on the computer sharing the media. 

anyway thanks guys

nick.

---

### Post by tallman9 on 2007-03-11
try smb4k, it's really easy to use it...
> Description: A Samba (SMB) share advanced browser for KDE
 Smb4K is a SMB (Windows) share browser for KDE. It uses the Samba software
 suite to access the SMB shares of the local network neighborhood. Its purpose
 is to provide a program that's easy to use and has as many features as
 possible.

---

### Post by necco on 2007-03-11
got similar issue mounting remote shares on my LAN, linneighborhood and smb4k report a problem with smbmnt that should work from root. NB i have no smbmnt package installed nor is available from repositories (hedgy 2.6.11)

---

### Post by Mr. C. on 2007-03-11
I don't know anything about the smb4k product, but I can see some potential for confusion in terminology.  That suite uses the term "browser" in the same fashion as Nautilus as a file system browser.

The term "browser" in Windows File and Print sharing means the service that collects the names of the resources on the SMB network, making them available for users to see (as in Network Neighborhood).

From here, I will only use the latter definition.

Windows makes resources known on a LAN by allowing each Windows station to attempt to act as a Master Browser.  If no other Master Browser exists, that station will win the election and become the Master Browser for that LAN.  The opposite is that a MB already exists, and the station attempting to become the MB will lost the election, UNLESS it is configured with a higher priority, in which case it will win.

The point of these explanation, is that it should be clear now that there needs to be at least on MB on an SMB network, for File and Print shares to appear.  If you are using Samba as your file server, and systems come and go from the network, you probably want to tell Samba to become the MB; otherwise, it will take time for any newly connected Windows station to become the MB and make shares known (again, as in via Network Neighborhood).

The configuration settnigs in Samba's smb.conf file that you need to learn about are "domain master" and "local master".  See:

[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#DMB](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#DMB)

MrC

---

### Post by drpepper on 2007-03-12
thanks for everyone's replies. mr.c has got the right idea, i dont want another program like nautilus, or network neighborhood to look thru the network. I want the shares on the network to be mounted to a directory say /media/shares, with no input from the end user. In mythtv you can only set one dir as the 'Video' directory, so i was thinking of creating a link to /media/shares within the video ("/media/Video") directory, so if any shares are available they will be visible to mythtv. Then is there is no shares it simply will be an empty directory.

nick

---

