---
title: "File Sharing between remote sites"
date: 2018-12-04
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2018-12-04
I have two remote sites. Each site has it's own file servers and local file sharing. The workstations at each site are Windows. Each site has approximately 2TB of files which could potentially be accessed by up to 10 users. For a long time these sites operated independently from each other. We are now seeing much more need for the sites to access the same data.

What would be the preferred way to share the files so that either site could access the information one the other, preferably using tools in the Standard Ubuntu distribution and WIndows desktops.

---

### Post by QIII on 2018-12-04
How are the workstations currently gaining access to the resources?

SSH/PuTTY?
A web interface?
Something else?

---

### Post by rsteinmetz70112 on 2018-12-05
Samba is running locally  at each site. Backups are made of each site with rsync.
The two sites do not currently share resources with each other. They are accessible using Putty, usually only for remote administration.
I do have limited public IPV4 addresses for reach site and could go to IPV6 although I haven't yet.
They are served by different ISPs

---

### Post by mitesh.agrwl on 2018-12-05
> **rsteinmetz70112 said:**
> Samba is running locally  at each site. Backups are made of each site with rsync.
The two sites do not currently share resources with each other. They are accessible using Putty, usually only for remote administration.
I do have limited public IPV4 addresses for reach site and could go to IPV6 although I haven't yet.
They are served by different ISPs

If one static IP is available at each site, one option is to establish a site-to-site IPsec VPN with NAT. VPN provides access to remote local network with all the available resources on that network. Please ensure that both of those local networks have different IP network, i.e. if one site is using 192.168.0.1/24, other should not use the same network.

---

### Post by rsteinmetz70112 on 2018-12-05
If we used Samba for file sharing would the Samba Domains for both sites need to be the same?

---

### Post by mitesh.agrwl on 2018-12-05
> **rsteinmetz70112 said:**
> If we used Samba for file sharing would the Samba Domains for both sites need to be the same?

Yes, they will need same domain to access the shared files, but there can be one domain controller only, You can find the required information [here]("https://wiki.samba.org/index.php/User_Documentation").

---

### Post by rsteinmetz70112 on 2018-12-05
Having multiple domain controllers would be OK. They could act as backups to each other. I would need to change the domain at al least one site.

---

