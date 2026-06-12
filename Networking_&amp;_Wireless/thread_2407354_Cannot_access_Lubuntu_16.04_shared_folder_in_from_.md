---
title: "Cannot access Lubuntu 16.04 shared folder in from Windows 10"
date: 2018-12-03
forum: Networking &amp; Wireless
---

### Post by Paddy Landau on 2018-12-03
For a while, I've been unable to access my Lubuntu 16.04 shared folder from Windows 10.
In Windows 10 > File explorer > Network, the Ubuntu 16.04 machine simply doesn't show up.

What I have on my Lubuntu machine:


[LIST]
[*]Both machines are on the same network, connected to the same router via Ethernet.
[/LIST]


[LIST]
[*]The Lubuntu machine has a folder named [FONT=lucida console]/public[/FONT], which has full permissions, i.e. [FONT=lucida console]chmod[/FONT] [FONT=lucida console]a+rwx[/FONT].
[/LIST]


[LIST]
[*]The [FONT=lucida console]/public[/FONT] folder is mounted with fuse via [FONT=lucida console]/etc/fstab[/FONT], which forces full public permissions on all folders and files within it. Here is the line from [FONT=lucida console]/etc/fstab[/FONT].
```
/public /public fuse.bindfs force-user=nobody,force-group=nogroup,create-for-user=nobody,create-for-group=nogroup,create-with-perms=ugo+rwD,chmod-ignore,chmod-allow-x,chown-deny,chgrp-deny,perms=ugo+rwD 0 0
```
[/LIST]


[LIST]
[*]Samba is installed, and [FONT=lucida console]/etc/samba[/FONT] contains the following lines, having used [FONT=lucida console]testparm[/FONT] to check and reformat.
```
[public]
        comment = Public on Elise
        path = /public
        read only = No
        create mask = 0666
        directory mask = 0777
        directory mode = 0777
        guest ok = Yes
```
[/LIST]
I don't know what else to do. Please help.

---

### Post by Morbius1 on 2018-12-03
>  In Windows 10 > File explorer > Network, the Ubuntu 16.04 machine simply doesn't show up.

Find the host name of your Linux box:
```
hostname
```
Then in Win10 don't browse for the machine ask for it explicitly by it's mDNS qualified host name:
```
\\hostname.local
```
Does that work?

---

### Post by Paddy Landau on 2018-12-03
@Morbius1, [FONT=lucida console]//Elise[/FONT] without [FONT=lucida console].hostname[/FONT] worked.

Thank you! I've pinned it to my "Quick access" in Windows.

And now I realise that I can't access my Windows 10 public folder from my Lubuntu :(
I'll do some investigation.

---

### Post by Morbius1 on 2018-12-03
> And now I realise that I can't access my Windows 10 public folder from my Lubuntu
Win10 will disable SMBv1 on the server side if you've kept it updated. Lubuntu 16.04 can only access the server with SMBv1 so what you are seeing may be a dialect issue.

To find out edit /etc/samba/smb.conf and right under the "workgroup = WORKGROUP" line add this one:
```
client max protocol = SMB3
```
Restart smbd:
```
sudo service smbd restart
```
Then try to access the share again.

---

### Post by Paddy Landau on 2018-12-03
Thanks, Morbius1, but unfortunately that didn't work. I restarted both machines after making the change.

Lubuntu sees that there is a Windows network, but Nautilus displays nothing when I go to it.

Don't worry, because it's more important for me to access Lubuntu from Windows than vice-versa.

Thanks again.

---

