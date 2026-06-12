---
title: "Protocols to link up with NAS: which is better?"
date: 2014-10-18
forum: Networking &amp; Wireless
---

### Post by cecilieaux on 2014-10-18
I recently purchased a Seagate Central NAS and now file manage gives me several options to connect to it, including afp:// (???), smb:// , [ftp://,](ftp://,) sftp:// protocols. 

Anyone have any recommendations as to which is better, safest, fastest and will make me rich, famous and attractive? ;)

Thanks in advance for your help!

---

### Post by tgalati4 on 2014-10-18
afp is for appletalk file transfer protocol.  That may be helpful if you have older macs on your network.  The shares would automatically show up in Finder.

smb is SAMBA and is useful for Mac, Linux, Windows.  ftp is unsecured, simple file transfer protocol.  This is not recommended.  sftp is secure ftp and is only needed for scripts and some programs that can only use sftp for transfer.  

So smb is probably what you want.

Let us know how well the Seagate Central NAS works.  Most NAS firmware sucks.  Perhaps this one maybe different.  You will know shortly.  I would keep a bucket handy.

---

### Post by cecilieaux on 2014-10-25
Will try and report back. Sorry, could not get back to this sooner. Life ...

---

### Post by cecilieaux on 2014-10-26
> **tgalati4 said:**
> afp is for appletalk file transfer protocol.  That may be helpful if you have older macs on your network.  The shares would automatically show up in Finder.

smb is SAMBA and is useful for Mac, Linux, Windows.  ftp is unsecured, simple file transfer protocol.  This is not recommended.  sftp is secure ftp and is only needed for scripts and some programs that can only use sftp for transfer.  

So smb is probably what you want.

Let us know how well the Seagate Central NAS works.  Most NAS firmware sucks.  Perhaps this one maybe different.  You will know shortly.  I would keep a bucket handy.

OK, I tried smb and I get asked about a workgroup and I freeze. I have read a samba tutotial and it's complicated for me. I'm not sure which is the client and which the server. Essentially, I got the NAS as storage for stuff in three computers at home one desktop and one laptop, both running Linux, and one laptop running Windows 7. I also liked the idea of remotely being able to log on and up- and download, (but that isn't working out very well, either).

Is there a SIMPLE tutorial for non-geeks somewhere that includes figuring out which is you server and which is your client?

---

