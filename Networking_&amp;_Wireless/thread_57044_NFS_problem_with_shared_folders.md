---
title: "NFS problem with shared folders"
date: 2005-08-15
forum: Networking &amp; Wireless
---

### Post by ubuntu-nerd2005 on 2005-08-15
Hi

I have a ID10T error I need to sort out.

I have messed up my network configuration trying to get it to work.

I have a home network consiting of a server, 3 Ubuntu machines, and a Winblows machine.

I have setup samba and had it working so the winblows box could log in to all the ubuntu machines and vice versa.

However I could not connect between ubuntu machines using samba and wanted to use NFS anyway.

So I set up nfs.

Basically i have a shared folder in /home called /public.

Anyway when I got into shared folders and select to share this folder with NFS on my home network it causes shares admin to do a wobbler.

It stops working. From CLI I get:

williamgates@morpheus:~$ gksudo shares-admin
(shares-admin:8608): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

After this the machine stops commicating on the network (it is no longer in the list of network servers.

I guess I need to find out what is being screwed up when i add a shared folder for NFS and where it is located.

If anybody can help me with this I would greatly appreciate it.

I am sure you should be able to share a folder over both nfs and samba? Right?

Anyway look forward to hearing what people can advise me on this

Cheers

John

---

### Post by ubuntu-nerd2005 on 2005-08-15
Must be a tricky one judging from the response...

Gave I asked this in the right place?

---

