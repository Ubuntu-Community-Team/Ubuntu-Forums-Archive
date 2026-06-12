---
title: "Unable to change permissions to folder"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by jimmy2975 on 2007-09-09
Hi, 

I am new to linux.

I am sharing my partitions on Fedora desktop with my Ubuntu laptop using the following command
 mount -t cifs -o username=bbbbb,password=kkkkk //share /mnt point over the wireless home netowrk

I can read the folders fine but I am not able to delete/write to it. I have tried to find how to change permissions but cant quite figure it out. 

Any help is appreciated.

Thanks
Jimmy

---

### Post by kidders on 2007-09-11
Hi there & welcome,

Since you're sharing your files using Microsoft's networking protocols, the permissions you're trying to change probably don't really exist ... so attempting to change them won't have any effect. Is there a reason you're sandwiching a third party protocol between two Linux boxes?

It looks as though what you've done is taken two computers that speak the same language and...[LIST]
[*]Mapped file names, ownership & permissions from their "real" states on your server to an artificial representation in a completely different filesystem model, in such a way that retains as much of the original information as possible.
[*]Since Microsoft operating systems don't support the traditional *-nix 8-bit access control model, and can't handle as wide a range of filenames as Linux can, some of that information is lost.
[*]On the client, the Microsoft filesystem model is mapped back to the Linux world. Since Linux lacks support for a variety of *it's* properties (eg case insensitivity, the "archive" file attribute, and so on), more information may be lost at this stage.
[*]At this point, you attempt to execute "chmod", for example, on one of the server's files. Naturally, without some very careful configuration, there is no way something like that will necessarily work as expected, because a file's permissions (as seen by the client) are largely a product of invention and guesswork, rather than something that really exists.[/LIST]In general, Samba will always try its best to avoid allowing access to a file by someone who probably shouldn't have it. As a result of all the unnecessary mapping that's taking place between your two boxes, all of the following will probably have to be true, to *guarantee* you write access to files...[LIST]
[*]You will have to mount the remote share on your client box using a Samba username that maps to the Linux user you're logged in as.
[*]That Samba username must map to the *server's* Linux user that owns the files you're trying to access (ie preferably you).
[*]On the server, the Linux user accessing the files must have write access to them (which is highly likely if he owns them).
[*]The Samba server must not be configured to override its own Linux filesystem's permissions ... something which is very often done to create things like "read only" public shares, for instance.[/LIST]Since you've provided no information about your Samba configuration, or the filesystem you're trying to access, it's hard to be any more specific than that, I'm afraid. There are lots of very good reasons for using Samba to share files between Linux boxes, but if you don't have one, I would suggest switching to NFS, to eliminate all the irritating (and thoroughly confusing) filename & access control nonsense. It can be quite a hassle.

I hope that helps.

---

