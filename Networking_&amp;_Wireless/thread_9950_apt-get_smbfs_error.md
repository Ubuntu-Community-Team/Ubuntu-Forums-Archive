---
title: "apt-get smbfs error"
date: 2005-01-03
forum: Networking &amp; Wireless
---

### Post by uncleyap on 2005-01-03
I read here that smb mounting does not work until we do apt-get smbfs

So I tried. But this is what I got:

[B]$ sudo apt-get install samba

Password:
Reading Package Lists... Done
Building Dependency Tree... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jinghe@jinghe-eqs:~ $ sudo apt-get install smbfs
Reading Package Lists... Done
Building Dependency Tree... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package smbfs has no installation candidate[/B]


 :confused: 

Can any one please highlight what I did wrongly?

 :D  :-&

---

### Post by hardcandy on 2005-01-03
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)         add the repositories


[http://ubuntuguide.org/#installsamba](http://ubuntuguide.org/#installsamba)                 you had the right command but the repositories you were using did not have the package. Some other nice simple instructions in that unofficial guide, I reccomend using it.

---

### Post by uncleyap on 2005-01-04
I found your information very useful.

I had forwarded it to the end user.

Thanks!

 =D>

---

