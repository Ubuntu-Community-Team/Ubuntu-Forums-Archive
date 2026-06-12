---
title: "problem mounting network drive"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by simonsimon on 2007-01-26
Hi

I'm trying to follow this how to:

[http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)

but I'm getting this error:


```
[mntent]: line 12 in /etc/fstab is bad
```

Here's the line that is supposedly bad:

```

//insertech-dc.INSERTECH.NET/Network\ Drive /media/Network\ Drive cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```


Can anyone tell me what I've mistyped? 

Here's some more info.  I'm at work on Edgy trying to connect to a folder on my windows server.
As far as I know I've done everything the "how-to" said I should do...including installing samba and smbfs.

Thanks in advance.

---

### Post by simonsimon on 2007-01-26
It seems like the actual problem is that the share name is two words "Network Drive".

I can successfully mount a network folder like this:

```
//10.0.0.3/New /media/network cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

But if I try anything like this:

```
//10.0.0.3/Network\ Drive /media/network cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```
```
"//10.0.0.3/Network Drive" /media/network cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

It doesn't work.

What's the correct way to enter a folder name with a space in it in nano?

Thanks.

---

