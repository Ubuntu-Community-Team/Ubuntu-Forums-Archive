---
title: "SAMBA: Mapped drive fails but UNC access ok! in 8.10"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by cmkeane on 2008-11-05
I have configured samba on dozens of machines, but I have run  into a total head-scratcher with a new 8.10 install.  I am trying to set it up as a standalone server to provide public shares to a closed network. 

I can access all the shares and files by using the UNC from my WinXP and Vista machines - say \\servera\data

But if I map this share to a drive, I always get an "Access Denied" error. I have even tried setting it up as a PDC, etc and doing the net group add exercises, and the tdbsam has the right username, etc (as seen by accessing it via UNC).

I really need to be able to map it to support some legacy software.

---

### Post by bab1 on 2008-11-05
> But if I map this share to a drive, I always get an "Access Denied" error.  This may be an encryption problem. See [[COLOR="Red"]**this**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=954691")

---

### Post by cmkeane on 2008-11-06
Thanks, but that doesn't seem to be the issue.

So:

1. In WinXP and Vista from the run menu, I can:
//servera/data and access all of the files fine.

2. In ubuntu I can smbclient to //servera/data w/o any authentication at all

3. In ubuntu I can mount -t cifs //servera/data w/o any problems

4. But if I map //servera/data to a drive letter, say N: in WinXP or Vista, I get "Access Denied."

I can mount other linux servers (FC and Ubunut 8.04) running samba on these windows machines  and map the drives fine, so I am doubtful its a windows setting. 

I am not seeing any errors in various samba logs either, and I have the loglevel turned up to 3.  

I'm totally lost on this now.

---

### Post by uzi09 on 2009-05-21
It'd help if you would share your /etc/samba/smb.conf file.

It may be a similar issue I've had before, but instead of a ton of Q&A & much confusion, sharing the file would allow us to just see what the problem is right away.

If possible, an **ls -l** of each folder shared would be nice as well so we can see what the permissions are like.

---

