---
title: "Beginner OpenVPN Question"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by jcws6 on 2007-04-23
I'm looking for a way to securely share a folder with Windows, and OpenVPN seems to fit what I need.  My problem is - I want access to the share from _any_ Internet-connected PC.  Does that capability exist in OpenVPN?  I saw the part about creating per-client keys, and got confused (I won't always know the name of the computer I'm at).

Any help would be GREATLY appreciated.

---

### Post by jcws6 on 2007-04-23
It looks like what I'm looking for is an OpenVPN setup with a Public Key Infrastructure (PKI), instead of a Static Key.  Any information on PKI?  Or maybe I can SSH into the server & generate the Static Key there, whenever I need it?  Man, this is confusing!

---

### Post by n8wood on 2007-04-23
You could only do this with OpenVPN if you are able to install the ovpn packages and certificates. A much easier solution would be to setup SSH and use an SCP client to access the files. In Linux you could use gftp, in Windows WinSCP. That would give you drag/drop functionality or you could mount it as an SSHFS share.

---

### Post by jcws6 on 2007-04-23
I'm interested in speed as well as security, and I've read SSHFS is slower than VPN.  Any truth to that?

---

