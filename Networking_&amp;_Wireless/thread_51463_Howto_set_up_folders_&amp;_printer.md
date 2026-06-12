---
title: "Howto set up folders &amp; printer"
date: 2005-07-24
forum: Networking &amp; Wireless
---

### Post by jrev on 2005-07-24
Hi all,

Where can I find a practical (step by step) howto on files sharing with ubuntu 5.04 ?

Thanks  :) :)

---

### Post by majikstreet on 2005-07-24
[QUOTE=jrev]Hi all,

Where can I find a practical (step by step) howto on files sharing with ubuntu 5.04 ?

Thanks  :)[/QUOTE]
 [http://ubuntuguide.org/#installsamba](http://ubuntuguide.org/#installsamba)

And

[http://ubuntuguide.org/#sharefolderstheeasyway](http://ubuntuguide.org/#sharefolderstheeasyway)

Hope that works.

---

### Post by jrev on 2005-08-18
Is samba the right app.to share files between 2 ubuntu OS ? 
I know it works windows/ubuntu or ubuntu /windows

---

### Post by siebzehn on 2005-08-18
[QUOTE=jrev]Is samba the right app.to share files between 2 ubuntu OS ? 
I know it works windows/ubuntu or ubuntu /windows[/QUOTE]

Hi,

To share between to linux OS, I would go with NFS, or FISH

NFS
[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)
[http://nfs.sourceforge.net/nfs-howto/server.html](http://nfs.sourceforge.net/nfs-howto/server.html)

FISH
All you have to do is type:  fish://servername_or_ipaddress   in the konqueror url bar (not sure if it works in nautilus because I use kde)

And for printers, use CUPS

---

### Post by jrev on 2005-08-19
Yes we have a tuto on this procedure :

[https://wiki.ubuntu.com/NFSServerHowTo](https://wiki.ubuntu.com/NFSServerHowTo)

but there is some discrepancy on the first paragraph :

Procedure

   1.      By default, the portmap service is only accessible on the local system. For NFS service to work, access must be allowed from NFS clients as well. Edit the file /etc/default/portmap and remove the -i 127.0.0.1 option from ARGS 

in fact there is no portman file in the /etc/default/ folder 

there is a portman file in /etc/init.d/ only after you installed the portman package from synaptic & thisis not indicated in the tuto

---

### Post by jrev on 2005-08-21
Has anybody already shared files between 2 PC's both under ubuntu 5.04 (Hoary) ?

If yes, I would be glad to hear how ?

with NSF or with samba ?

it seems that the NSF howto is not updated for Ubuntu Hoary

---

### Post by jrev on 2005-08-25
not so many customers ! ...

---

### Post by s_p_a_r_k_y on 2005-08-25
I have networked many companuters via samba before and use it at home with 5 linux computers and 1 windows machine. Samba works fine via Linux to linux and I think its a tad bit easier to setup than NFS, in fact it should take 5 minutes or less to edit the config file, /etc/samba/smb.conf

Just make sure you put them all on the same workgroup

---

