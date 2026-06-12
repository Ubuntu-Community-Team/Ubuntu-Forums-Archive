---
title: "Samba update changes smb.conf, keep local version?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by BassKozz on 2009-01-19
When I update Samba on my various machines the installer asks me if I want to keep the local version (old) or replace with the package maintainers version (new), I always choose to "Keep the local version" as I have customized it to my liking.

[LIST=1]
[*]Is there any problem with that? 
[*]Am I missing out on new features by choosing that?
[*]How can I go back (after the install) and check the differences between package maintainers vs. local?
[*]Is there a way to merge the new features but leave my custom settings uninterrupted?
[/LIST]

TiA,
-BassKozz

---

### Post by cariboo on 2009-01-19
I have been using essentially the same /etc/samba/smb.conf file for about 7 years. I always have a backup of the current version. If there is an update released or a new version, I usually let the install script install the maintainers version then run [diff]("http://unixhelp.ed.ac.uk/CGI/man-cgi?diff") against it and my custom version. If there is anything new I integrate it into my version if I need it.

I have a rather simple setup, I just need to be able to access the server from any computer on the network, and I'm not to worried about internal network security. 

Jim

---

### Post by BassKozz on 2009-01-19
Thanks for the input cariboo907,

Now that I've already elected to "keep my local version" and the upgrade has already happened, is there any way to see what the package maintainers version looks like?

---

### Post by BassKozz on 2009-01-20
:bump:

---

### Post by trentmc on 2009-01-20
this is a bit of a guess ... but have a look at /usr/share/samba/smb.conf

this "may" be the new version

others can correct me if my guess is way off ;)

---

