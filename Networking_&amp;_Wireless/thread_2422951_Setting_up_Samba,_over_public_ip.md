---
title: "Setting up Samba, over public ip"
date: 2019-07-15
forum: Networking &amp; Wireless
---

### Post by fredy50 on 2019-07-15
Hello People.

I'm setting up an ubuntu server. I'll setup samba service so i can access the share folder from everywhere.

But I have a raspberry pi 3 it works inside my network. Now I'll setup outsite my home network, but I can't access it.

I'm useing iptables for firewall

Please give me a good advice :)

---

### Post by TheFu on 2019-07-15
How do I say this nicely.

_**This is a really bad for security idea.**_ NEVER allow any Microsoft storage protocol to be used over the internet. They aren't secure.
Don't.

If you want to access storage from anywhere, use sftp, scp, sshfs, ssh tunnels or setup an openvpn.  There are good sftp clients that support ssh-keys for every platform that has a network stack.

ssh is a secure protocol that is suitable for local and remote use thanks to strong encryption.  On your secured LAN, you can use passwords with it, but over the internet, NEVER allow passwords as the only means of authentication.  That applies to any services accessed over the internet, not just sftp, ssh, HTTP, or any others you may have heard about.

ssh is the secure, swiss-army-knife for having systems communicate.  Know it. Use it. Love it.

---

### Post by him610 on 2019-07-16
Read an article a couple of weeks ago,  computer networks at NASA JPL got hacked through an unsecured Raspberry Pi.

---

### Post by uRock on 2019-07-16
> **fredy50 said:**
> Hello People.

I'm setting up an ubuntu server. I'll setup samba service so i can access the share folder from everywhere.

But I have a raspberry pi 3 it works inside my network. Now I'll setup outsite my home network, but I can't access it.

I'm useing iptables for firewall

Please give me a good advice :)

My guess would be the router not forwarding ports. That said, I'd heed TheFu's advice and set up a different protocol.

---

