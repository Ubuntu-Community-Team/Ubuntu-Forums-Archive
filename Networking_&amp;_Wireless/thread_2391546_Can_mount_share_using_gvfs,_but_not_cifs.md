---
title: "Can mount share using gvfs, but not cifs"
date: 2018-05-10
forum: Networking &amp; Wireless
---

### Post by bclavery on 2018-05-10
I'm a new Linux user trying to mount a Buffalo NAS so it can be backed up on with the Crashplan software.  The Crashplan software can't access the gvfs share location, so I'm trying to mount using cifs.

I can mount in Gigolo, or by terminal using:
gfvs-mount smb://192.168.100.158/cce

The NAS is then mounted to /run/user/1000/gvfs/smb-share:server=192.168.100.158,share=cce

There is no user name or password.  I can also access this backup in Windows 10 without any username or password.

Unfortunately Crashplan can't access this location, so I'd like to mount using cifs to /media/backup

I tried:
sudo mount -t cifs //192.168.100.158/cce /media/backup

It asked for password and I gave it the sudo password, but got:
mount error (22): invalid argument

So I tried:
sudo mount -t cifs //192.168.100.158/cce /media/backup -o guest

no password prompt this time, but still got:
mount error (22): invalid argument

The location /media/backup/ exists.

Any idea what I'm doing wrong?  I suspect it is a permission issue, but not sure.

Thanks,
Brian

---

### Post by Morbius1 on 2018-05-10
The one thing you didn't tell us is what version of Ubuntu you are using. It makes a difference.

If you are using say Ubuntu 16.04 then gvfs will use smb1 to access the NAS. But CIFS will use SMB3 so you might want to change your cifs mount statement to this:
```
sudo mount -t cifs //192.168.100.158/cce /media/backup -o guest,vers=1.0
```
THe vers=1.0 will force the smb dialect to SMB1.

One other thing and it depends on how old the version of samba that is being used on the NAS but you might need to pass another option to set it to an earlier security version:
```
sudo mount -t cifs //192.168.100.158/cce /media/backup -o guest,vers=1.0,sec=ntlm
```

A cifs mount usually takes a bit of trial and error with a NAS because you don't know how it's configured.

---

### Post by bclavery on 2018-05-11
Thank you.  I'm on Ubuntu 16.04 and was able to mount the NAS with that first line of code, 

sudo mount -t cifs //192.168.100.158/cce /media/backup -o guest,vers=1.0
but it's still asking for my password.  I entered my sudo password and it mounted the NAS.  I thought that the "guest" switch disabled that.  Ultimately, I'd like to add a line to the fstab to have it mount at startup and don't want to type a password.

---

### Post by bclavery on 2018-05-11
Got it by adding "sec=none" instead of "sec=ntlm".  Thanks again

---

