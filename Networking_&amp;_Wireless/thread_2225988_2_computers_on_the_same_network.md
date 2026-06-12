---
title: "2 computers on the same network"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by john_ellis2 on 2014-05-24
Hi All,

I am not sure that the title is very good but this is my problem.

I have a desktop computer and my wife has a laptop.

I am sick and tired of putting files on a data stick to give to my wife so she can have them on her computer.

We both use Ubuntu 13.10, is there any way we can connect our computers via the wifi router / network to share files or even message each other.

Thanks very much

John

---

### Post by Bashing-om on 2014-05-24
john_ellis2; Hi !

There are lots of ways to do that .. this is the easiest: - as we are talking 'bubtu 2 'buntu :
[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449)

[INDENT][INDENT]just my little bit
[INDENT][INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by john_ellis2 on 2014-05-24
Thank you for the reply, your a star.

John

---

### Post by oldfred on 2014-05-24
Bashing-om's link to suggestion of SimpleHTTPServer looks interesting.

I originally used Samba as I had XP on laptop and Ubuntu on desktop. And that was frustrating as Windows updates, firewall updates, other updates and reinstalls of Ubuntu had me resetting thing continuously. So I installed Ubuntu on laptop and then went with NFS. 

I created some scripts. One when I update install to add NFS configuration to a new install, one to mount partitions and one to rsync folders between them. It turns out to only be a few commands but addresses must be consistent or you have to edit them or DHCP may be an issue, unless you either fix address.

HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

If interested in details I can post the commands I run. 

Some have also posted that SSH  is a better way.
This is syncing /home, but you can just sync a folder.
HowTo: Use Grsync and OpenSSH to sync your /home directory over a network
[http://ubuntuforums.org/showthread.php?t=795668](http://ubuntuforums.org/showthread.php?t=795668)

---

### Post by john_ellis2 on 2014-05-24
Hi OldFred,

My wife looked at me like I was speaking another language when I was trying to explain the first way of file sharing so I am looking at setting up file sharing with samba, I will post a reply on how I get on.

Cheers for the replies everyone.

John

---

### Post by Bashing-om on 2014-05-24
john_ellis2; Hey;

It is doable, however, samba is a protocol to share with for Windows, and is overkill in this instance.

If ya want, just enable "file sharing" on a directory (right click) on each machine and you are done. Access the file share from the browser window.

I am a firm believer in
[INDENT][INDENT][INDENT]The kiss principal
[/INDENT][/INDENT][/INDENT]

---

