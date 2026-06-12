---
title: "Mount a Network Hardrive"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by Mr_Marc on 2008-02-06
How do I make a permanent mount for a network hard drive?

I can manually mount it doing sudo mount //ipaddress/share /mnt/windows/ -o username=xxxxxx,password=xxxxxx, dmask=777,fmask=777

and this in the fstab 

Thanks Marc...

---

### Post by kevinatkins on 2008-02-06
Hi,

Oops - see edit below...

I'm assuming you're using a network drive that is shared over Samba?

If so, I've got a similar setup. I installed smbfs, then added the following in my /etc/fstab

```

//landisk/public /network       smbfs uid=kevin,gid=kevin,rw
```

... obviously change certain bits to match your installation, but hopefully that should give you the idea.

It works well - mounted automatically at boot, and I use it to store all my music!

EDIT: 

OOPS! Sorry, I didn't refer to your screenshot. Well, it should be working for you. What happens if you issue a 'sudo mount -a' command?

---

### Post by Mr_Marc on 2008-02-06
I tried changing it but i get the error see screen shot

---

### Post by kevinatkins on 2008-02-06
Hmm,

I'm wondering whether this could be a problem with the setup of your shared storage device? Are you able to connect to it from a Windows machine?

---

### Post by Mr_Marc on 2008-02-06
Yes and ever other computer on the network. I can connect to the folder under places.
from Ubuntu

---

### Post by kevinatkins on 2008-02-06
This is strange. Are you sure you've got smbfs installed? I'm going to have to leave it for tonight - getting late in the UK...

---

### Post by Mr_Marc on 2008-02-07
Kind of strange. How would one tell if smbfs are installed??

I can see the drive in "places" - "network" I can read and wright to the drive no problem.

Just can't get it to mount. 

I am new to Ubuntu and Gnome about 2 weeks. 

Thanks for your help..

Marc...

---

### Post by Mr_Marc on 2008-02-07
Problem resolved. I had not installed SMBFS I corrected that and everything is working great.

Thank for your help in this matter.

Marc...

:guitar:

---

### Post by kevinatkins on 2008-02-07
Glad you got it sorted. All that smbfs does is allow you to mount samba shares into your existing filesystem; it's possible to browse shares without it (as you found by going to Places -> Network) though..

---

