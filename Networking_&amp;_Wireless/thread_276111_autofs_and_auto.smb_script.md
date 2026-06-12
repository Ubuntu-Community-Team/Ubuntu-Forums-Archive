---
title: "autofs and auto.smb script"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2006-10-12
Does anyone use autofs to automatically mount samba shares? As I understand auto.smb is a script which is supposed to look up available samba shares and mount them. But it does not work for me.

I put the following in the auto.master file:
```
/mnt/auto /etc/auto.smb --timeout=60 --ghost
```
made sure that auto.smb is executable and do
```
sudo /etc/init.d/autofs restart
```

But I have nothing in /mnt/auto mounted. Maybe I want too much from it?

---

### Post by foxy123 on 2006-10-13
Am I right to assume that no one really uses autofs in general and auto.smb script in particular?

---

### Post by iZm on 2006-11-08
I use autofs to mount shares at work and when at home over the vpn.

My auto.master contains the following line.

> /home/nige/Documents/institute/mounts  /etc/auto.institute  --timeout 5 --ghost -v

and I created, "auto.institute" (I work for the NHS Institute for Innovation and Improvement) with the following two lines...

> home -fstype=smbfs,username=username/domainName,password=myPassword,uid=nige,gid=users,fmask=0775,dmask=0775     ://hostname.domain.name/home
shared -fstype=smbfs,username=username/domainName,password=myPassword,uid=nige,gid=users,fmask=0775,dmask=0775   ://hostname.domain.name/Shared


I use the full domain name in the server name because smb name services aren't very good over a vpn. If your share is always local, you can just use the netbios name alone, or the IP address.

make sure to install smbfs too.

Because I use the above config, I haven't bothered figuring out how to interact with the auto.smb script yet. :???:

---

