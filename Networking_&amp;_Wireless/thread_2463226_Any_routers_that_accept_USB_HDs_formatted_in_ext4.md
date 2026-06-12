---
title: "Any routers that accept USB HDs formatted in ext4?"
date: 2021-06-06
forum: Networking &amp; Wireless
---

### Post by thumper76 on 2021-06-06
I have an unused 1T hard drive and I planned to use a USB adapter so I could plug in into my Linksys router. In reading the Linksys docs it says the router will only accept FAT, NTFS and HFS+ formats. As I understand it, Ubuntu would only read FAT. I'm certainly not going to format a 1T HD in FAT.  Are there any routers that accept a USB HD formatted in ext4? Or is there another solution?

---

### Post by coffeecat on 2021-06-06
> **thumper76 said:**
> As I understand it, Ubuntu would only read FAT.

Ubuntu reads from, and writes to, NTFS out of the box just fine, and has done for years. However, that is irrelevant in the situation you describe. It would be the router firmware that would be reading the HD, not Ubuntu. Ubuntu would access the data on the HD served by the router through a sharing protocol - I guess SMB.

---

### Post by thumper76 on 2021-06-06
OK, good to know about NTFS. I wasn't familiar with SMB, so I had to do some research. If they use SMB does that mean I will need to install SAMBA?

---

### Post by scorp123 on 2021-06-06
> **thumper76 said:**
>  Are there any routers that accept a USB HD formatted in ext4?

My Synology router works without problems with Ext4. But as others have already mentioned: This isn't even relevant. Since the disk will be attached to the router, it will be the router that does the reading and writing, in whatever file format. Your Ubuntu machine will only indirectly access the disk via a network file sharing protocol, e.g. SMB, NFS, SSH, SFTP or whatever, depending on how you set this up and/or what file manager you use. Most Linux file managers can already talk in SMB or SSH/SFTP, you just need to type in the network location into the file manager.

[ATTACH=CONFIG]288681[/ATTACH]

---

### Post by thumper76 on 2021-06-17
This is a follow up on my original  problem. I formatted the 1T hard drive in NTFS. SMB wouldn't work, but I was able to connect using password protected FTP. It seems to be just as fast as a local HD.

---

### Post by scorp123 on 2021-06-18
> **thumper76 said:**
> I was able to connect using password protected FTP. It seems to be just as fast as a local HD.

**[COLOR="#FF0000"]FTP protocol is NOT encrypted.[/COLOR]** Anyone in that same network (tech-savvy kids? Neighbours with access to your WLAN? etc.) **can read the password** in clear text each time you login. Too bad if you used that same password elsewhere too, because in that case they can now do all kinds of things to you...

Please do not use this outdated + unsafe dinosaur protocol.

If anything try setting up **SFTP **(... that "S" matters ...) which is encrypted and a lot safer, if your router supports it that is.

---

### Post by thumper76 on 2021-06-18
> **scorp123 said:**
>  Too bad if you used that same password elsewhere too, because in that case they can now do all kinds of things to you...

 

It's worst than that. The router won't accept SFTP and Linksys forces you to use the main router password as the FTP password! If Linksys is so oblivious to security on this, you wonder what other aspects of security they're ignoring.

---

### Post by scorp123 on 2021-06-18
> **thumper76 said:**
> It's worst than that. The router won't accept SFTP and Linksys forces you to use the main router password as the FTP password! 

Wow. Just wow. And "Ouch!!" #-o

---

### Post by TheFu on 2021-06-18
Let's think about this for a moment.
Connecting storage to a WAN router.  Does that seem like a good idea?

My common sense "smells bad" test says no.  Certain things don't make sense.

[LIST]
[*]Putting passwords onto the internet fails the "smells bad test."
[*]So does connecting any storage you don't intend to share with the world to a WAN router.
[*]Using plain FTP for any purpose in 2021 (really since 2002-ish) also fails the "smells bad test."
[/LIST]

For fun, google "router storage hacked".  See what I mean?  Last fall, a Netgear router was hacked the first day it were connected to the internet.  This has been an ongoing issue for the last decade.  Basically, every router company and most NAS companies that provide a way to either connect USB storage to the router or make the NAS storage available over the internet have been cracked - leaving the storage available to people around the world.

Fails the "smell's bad" test.

There are better options. Yes, they are nearly as easy, but they are 10,000,000x more secure.  Any Unix-like OS with USB storage on your LAN can be setup to provide remote access over ssh using ssh-keys. Don't allow passwords, only ssh-keys. when we setup ssh-server, we get scp, sftp and a bunch of other capabilities for free.  Every networked client OS today has a great sftp client program.  Don't confuse sftp and ftps.  One is good with strong authentication, the other is an SSL wrapper around plain FTP, typically with very poor authentication.   With sftp, any Linux client setup with ssh-keys (that's just 2 commands), can use almost any Linux file manager for access to the storage. It will use the ssh-keys automatically.  If you like, you can setup ssh-agent, so that unlocking the ssh-key need only happen once per login session.  If you don't logout of the client machine, it is easy to go for a week or a month without having to unlock the ssh-key via a password.  

Create an ssh-key and push the public version to another system: 
[Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386)

As for blocking internet brute force attacks, first, we disable passwords from source IPs outside our LAN, second, we install fail2ban which dynamically blocks offending source IPs after 3 or 5 failures.  The chances that any remote attacker would have your private ssh-key is extremely remote - nearly zero.  Plus, if you upgrade your key type from RSA to ed25519, then it is even more unlikely that any attacker will have the private key.

[https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278](https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278) has the ssh-keys and fail2ban and some other ssh security stuff.

Anyways, lots of possible solutions.  ssh is THE tool for how Unix-like OSes communicate. Remote access, remote control, tunnels, socks proxies, remote mount of file systems, backups, mirroring files, remote desktops ... and 50 other things.  All use ssh.

---

