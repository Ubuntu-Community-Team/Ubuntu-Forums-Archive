---
title: "Right Click Sharing - Gone"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by kman14 on 2008-12-17
When I was using Ubuntu 8.04, I'd set up Samba and could share the folders I wanted by right clicking and selecting the "Share" option.
This seems to have disappeared in 8.10.
Is there a simple way to do this or enable the right click "Sharing" option again?

Thanks.

---

### Post by kman14 on 2008-12-18
Sorry about the Bump, but I've looked through the forum and can't find anything.
Any help would be much appreciated.

---

### Post by kanikilu on 2008-12-18
So when you right-click in nautilus the "Sharing Options" context menu item is not there at all?

---

### Post by kman14 on 2008-12-18
Yep, it was there in 8.04 but not in 8.10 - though there's every chance that I've missed something.

---

### Post by chronographer on 2008-12-18
It is still there for me (using intrepid ibex and gnome)

---

### Post by albinootje on 2008-12-18
> **kman14 said:**
> Yep, it was there in 8.04 but not in 8.10 - though there's every chance that I've missed something.

I'm using 8.10 and the "Sharing Options" is there.

dpkg -l|grep samba
samba
samba-common

dpkg -l|grep smb
libsmbclient                             
libsmbios-bin                             
libsmbios2                                
qtsmbstatus-server                        
smbclient                                 
smbfs                                     

dpkg -l|grep nautilus-share
nautilus-share

---

### Post by kman14 on 2008-12-18
Clearly I've done something wrong.

When i typed "dpkg -l|grep smb" into the terminal I'm missing "qtsmbstatus-server".

Also "dpkg -l|grep nautilus-share", shows nothing.

I might try a re-install of Samba.

Thanks for the replies - I'm happy the problem's on my end and that they haven't taken out the "right-click" option.

---

### Post by badrunner on 2008-12-18
> **kman14 said:**
> Clearly I've done something wrong.

When i typed "dpkg -l|grep smb" into the terminal I'm missing "qtsmbstatus-server".

Also "dpkg -l|grep nautilus-share", shows nothing.

I might try a re-install of Samba.

Thanks for the replies - I'm happy the problem's on my end and that they haven't taken out the "right-click" option.

Sounds to me like you just need to install nautilus-share, find it in synaptic from the gui or aptitude install at the command line. The qtsmbstatus-server sounds irrelevant for what you want here.

FYI you will probably have to log out and back after install nautilus-share

---

### Post by albinootje on 2008-12-18
> **badrunner said:**
> Sounds to me like you just need to install nautilus-share, find it in synaptic from the gui or aptitude install at the command line. The qtsmbstatus-server sounds irrelevant for what you want here.

FYI you will probably have to log out and back after install nautilus-share

I agree, except a
```

killall nautilus

```
will probably be enough

---

### Post by kman14 on 2008-12-18
Thanks,

I'll give it a try and report back.



### That did the trick ###

---

