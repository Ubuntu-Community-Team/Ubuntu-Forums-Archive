---
title: "Connection issues to access shared folders on my linux server via Tailscale"
date: 2022-10-30
forum: Networking &amp; Wireless
---

### Post by johndid on 2022-10-30
Hi everyone,
I installed Tailscale on my Linux Ubuntu server 20.04 some time ago. I  also set a Route on it to access other devices in my LAN. Everything  seems to work properly and I can access a few services running on my  server via my smartphone browser by using their own LAN IPs and ports.  Great!
I would also have liked to acces my shared folders I set on my linux  server via my smartphone’s file manager as I did when I used to run  Wireguard only, but after I entered my credential and my Server’s IP -  where the shared folders lie -  and pushed “Connect”, I got a Connection  issue message. I haven’t yet figured out what the problem might  possibly be?
For the record, I disabled the firewall on my linux server, but nothing changed, same issue.
Could you please help me?
Thanks

---

### Post by TheFu on 2022-11-01
What protocol are you using for file sharing?  There must be 20 choices.  Please don't make us guess.
Some Android devices only support SMB1, which was old in 2002. Best to avoid it.

What I do is use nextcloud, but for direct Android to Linux/Unix file access is to setup **ssh-server** on all my Linux/Unix systems, which includes an sftp server.  Then on Android, I install **Ghost Commander** which supports sftp access.  sftp is very secure, assuming you don't use passwords.  But on a LAN, that should be good enough.  

Over the internet where security is completely different,  you'd want to setup ssh-keys and use those for authentication.  For me, I use nextcloud over a VPN from a phone when I need remote access.  From a laptop when I'm remote, accessing nearly any system on my different LANs is fairly easy using ssh-based methods with ssh-keys (I use ed25519 keys).  ssh-keygen is the command to create the keys on Unix systems.

---

