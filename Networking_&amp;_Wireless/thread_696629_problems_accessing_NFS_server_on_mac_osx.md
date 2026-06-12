---
title: "problems accessing NFS server on mac osx"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by bryantm on 2008-02-14
i am running mac osx 10.5.2 and cannot access my NFS shares. i can access them just fine on all the desktops (running linux of course) so i know its not a server issue. when i try and connect to the shares on the mac it just says im using an invalid user name or password....but i dont enter a password in on any of the machines..... any one know how to get this working on macs? it seems like i might need to do something to my /etc/exports to allow proper access to the mac

---

### Post by Eiríkr on 2008-02-22
> **bryantm said:**
> i am running mac osx 10.5.2 and cannot access my NFS shares. i can access them just fine on all the desktops (running linux of course) so i know its not a server issue. when i try and connect to the shares on the mac it just says im using an invalid user name or password....but i dont enter a password in on any of the machines..... any one know how to get this working on macs? it seems like i might need to do something to my /etc/exports to allow proper access to the mac

Hi there Bryantm -- 

This is a known problem in sharing via NFS between Linux and Mac.  Your user *name* might be the same on both machines, but the issue is that NFS shares *not* on the basis of names, but instead using user *IDs*.  If you open up a terminal and type in [font=courier]ls -l[/font], you'll see the contents of the current directory listed (the "ls" command) in long (the "-l" argument) format, which should show you the user names and groups for all non-hidden items.  Now type in [font=courier]ls -ln[/font] -- the additional "n" argument tells the ls command to show user and group ID numbers instead of names.  On Mac OSX, user and group names usually start at 501.  Meanwhile, on Linux, these ID numbers start from 1000.  This discrepancy is what's likely disallowing you from connecting -- NFS has no means for entering user names and passwords, unlike SMB Windows-style sharing, so if your Mac user and group IDs (UIDs and GIDs) don't match those on the Linux side, the connection will fail.  

One way around this is to install on your Ubuntu server not the nfs-kernel-server package, but instead the nfs-user-server package (these two are mutually exclusive).  The -user- version allows the use of UID mapping, so you can avoid mucking around with the complicated process of changing UIDs for existing accounts.  After installing the -user-server package, you'll need to add a "map_static=[filename]" entry in your /etc/exports file, with "[filename]" pointing to a map file with the format outlined at [[color=blue]this posting[/color]](http://www.usenet-forums.com/linux-networking/67613-nfs-map_static.html).

HTH,

Eiríkr

---

