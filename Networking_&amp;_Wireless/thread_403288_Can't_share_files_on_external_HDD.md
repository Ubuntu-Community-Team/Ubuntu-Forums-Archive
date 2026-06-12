---
title: "Can't share files on external HDD"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by tbuss on 2007-04-06
**Trying to share files across my network using Samba**
3 pc's all using Ubuntu

The files I'm trying to share are located on a [COLOR="Red"]external hdd[/COLOR]

I have [COLOR="Red"]mounted[/COLOR] the external hdd and installed [COLOR="Red"]ntfs-3g[/COLOR]

I can read and write to the external hdd with no problems.

I then enable sharing on the file I want to share (on external hdd)

I'll go to another pc on the network:  connect to server -> windows share -> IP address.
I can connect just fine, I even see the folder I want to access. When I try to access the folder it fails. It says the file might have been deleted, or just basically it cannot access the file.

So I tried the same procedure but this time with a file located on the internal hdd.
The share worked.

Is there something special I need to do so that other pc's can access shared files located on my external hdd? I found this, not sure if it will work because my hdd is a [COLOR="Red"]firewire [/COLOR]connection:

```
[usbdisk]
comment = Ekstern harddisk
path = /media/usbdisk
browseable = yes
read only = no
public = yes
```

---

### Post by tbuss on 2007-04-06
**If it helps here are the two shares I created as shown in smb.conf**

**This share fails:**
```
[Home_Productivity]
path = /media/External/Home_Productivity
available = yes
browsable = yes
public = yes
writable = yes
```
[B]
This share works:[/B]
```
[docs]
path = /home/tbuss/docs
comment = test share file
available = yes
browsable = yes
public = yes
writable = yes
```

---

