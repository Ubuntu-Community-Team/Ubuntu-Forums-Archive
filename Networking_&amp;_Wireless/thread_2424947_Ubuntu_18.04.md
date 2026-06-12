---
title: "Ubuntu 18.04"
date: 2019-08-17
forum: Networking &amp; Wireless
---

### Post by Major Payne on 2019-08-17
How do i disable Network Share discovery?

---

### Post by Morbius1 on 2019-08-20
I'm going to guess you mean samba / smb share discovery?

Temporarily?
```
killall gvfsd-smb-browse
```
Or Permanently?

** You could make it un-executable by ordinary users:
```
sudo chmod 744 /usr/lib/gvfs/gvfsd-smb-browse
```
** Or rename it so the system can't find it:
```
 sudo mv /usr/lib/gvfs/gvfsd-smb-browse /usr/lib/gvfs/gvfsd-smb-browse.disabled
```

THe problem here is that gvfsd-smb-browse is part of a package ( gvfs-backends ) that does a whole bunch of stuff so even though you can disable one component it might be re-enabled if there is an update to the package.

---

### Post by him610 on 2019-08-20
The OP did not state which version or distribution of *buntu he is using. There is the possibility that he may not have gvfsd-smb-browse installed. In my Xubuntu LTS 18.04.03 installation, there is no gvfsd-smb-browse installed; although, there is samba and several supporting files. I believe this is how to turn off / turn on samba for the current session. For a permanent solution, samba may be removed.
```

sudo service smbd stop
sudo service smbd start

```
Caveat: After second thought, my suggestions may not apply to your situation. It is probably the smb client that searches out the smb server.

---

### Post by Morbius1 on 2019-08-21
> In my Xubuntu LTS 18.04.03 installation, there is no gvfsd-smb-browse installed
Sure it is. It's not a stand alone package it's part of gvfs-backends. This is from a Live session of Xubuntu 18.04:
> xubuntu@xubuntu:~$ dpkg -L gvfs-backends | grep browse
/usr/lib/gvfs/gvfsd-afp-browse
[COLOR=#0000cd]** /usr/lib/gvfs/gvfsd-smb-browse**[/COLOR]
/usr/share/gvfs/mounts/afp-browse.mount
/usr/share/gvfs/mounts/smb-browse.mount


---

### Post by him610 on 2019-08-21
@Morbius1
You are correct. I was mistaken. It is also on my installation,
```

ll /usr/lib/gvfs/gvfsd-smb-browse
-rwxr-xr-x 1 root root 67576 Jul  5 09:04 /usr/lib/gvfs/gvfsd-smb-browse*

```

---

