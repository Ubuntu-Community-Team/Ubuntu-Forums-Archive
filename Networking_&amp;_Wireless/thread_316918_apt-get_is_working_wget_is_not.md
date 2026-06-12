---
title: "apt-get is working wget is not"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by xboxer21 on 2006-12-11
Hello,
I'm using a ubuntu edgy server which is behind a firewall and proxy. I have no problems using apt-get, however when i try to run wget a small file is downloaded with exactname as the actual file I'm trying to download, but it does not download the actual file.
I have also added export http_proxy=proxy.domain.com:8080 to .bashrc and its not helping.

any thoughts?

Thanks

---

### Post by Hendrixski on 2007-02-03
actually, I'm having a similar problem now.  wget just stopped working. Every pgp key I try to get crashes.  It's been working fine for about 4 months on this computer, and now it just stopped.  Any suggestions?

---

### Post by xboxer21 on 2007-02-04
Hendrixski,
I use SME server as my Gateway. I had dansguardian installed on the SME server, after uninstalling dansguardian on the SME server everything works now.

Thanks

---

