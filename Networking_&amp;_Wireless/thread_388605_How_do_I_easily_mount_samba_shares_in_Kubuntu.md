---
title: "How do I easily mount samba shares in Kubuntu?"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by dirtaholman on 2007-03-19
Hi all,

    I was wondering if there was a utiliy for Kubuntu similar to Ubuntu's connect to server option that will drop a link on my desktop to a samba share. I've seen the add a network folder wizard in the Remote Places, but it always gives me an error and refuses to connect.  It's a GNOME feature that I'm sure is in KDE somewhere, so I'd like to avoid the command line if possible.

Thanks in advance!

---

### Post by raja on 2007-03-19
If you want these always mounted, the best solution is to add them to fstab so that they are always connected while booting. [This]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html") is a pretty good tutorial on how to do that.

---

### Post by dirtaholman on 2007-03-19
Thanks for the response! However, I'm not worried about mounting it at boot. What I'm after is the desktop link to the share like how Ubuntu's Connect to server option under places does. I'm after a similar feature in Kubuntu without having to resort to the command line and playing with my fstab file.

---

### Post by dmizer on 2007-03-19
if you configure your mount directory in /media ... you will get a desktop icon.

for example:
```
//servername/sharename [COLOR="Red"]/media[/COLOR]/mountdirectory smbfs username=windowsuserename,password=windowspassword 0 0
```

though, i strongly suggest using cifs instead of smbfs.  it will allow for file transfers of over 2gb, and it will be faster.  for how to configure cifs in fstab, see the second link in my sig :)

---

### Post by dirtaholman on 2007-03-19
I was able to get it working after changing the share name, and it pops up on my desktop :-D. Not as pretty as how GNOME handles it, but I have too many people who get confused with it around me. Thanks again!

---

