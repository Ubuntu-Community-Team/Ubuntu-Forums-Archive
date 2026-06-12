---
title: "Samba as Primary Domain Controller for Windows network"
date: 2005-07-23
forum: Networking &amp; Wireless
---

### Post by hamish on 2005-07-23
Hello

I'm trying to setup my Linux server to host the profiles for my Windows clients. At the moment, all of my PCs and the linux server (which is the Primary Domain Controller) are connected through a Linksys router, which has DNS on it for resolving things like google etc. It does not resolve Internal PC names, as far as I know. I wouldn't expect it to.

I believe that i have set up my samba configuration correctly, as I followed a howto perfectly. However, when I try and add my Windows 2000 client to the domain, I get the error:

"The domain ZYZ is either invalid or does not exist"

It is the case that I need to set up my LInux server, which I have set up as the Primary DOmain Controller, to be a DNS server for the INTERNAL network?

Or, do I just set:
name resolve order = wins lmhosts hosts bcast

and run a WINS server on the Linux server?
When roaming profiles/active directory is setup on a Windows 2000 server, windows make that domian controller a DNS server.

If anyone can shed light for me, that would be great.

Hamish

---

### Post by hamish on 2005-07-23
hiya

 I have fixed the problem. It stemmed from my firewall.

the following ports are needed to be open (i have  enabled them only from sources in the local network)
udp: 137 138
tcp : 139 445
imcp: 3 and 4

Thanks
Hamish

---

