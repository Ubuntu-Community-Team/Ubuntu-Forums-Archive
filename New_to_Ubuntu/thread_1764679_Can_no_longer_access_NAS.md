---
title: "Can no longer access NAS"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by linux_believer on 2011-05-22
I somehow lost access to my NAS. I had samba installed previously and it just worked. Over a few months it worked fine then one day nothing. I thought with a fresh install it would correct the issue. Recently installed Natty and the problem still persist. Sometimes I cannot even see the NAS. See the attached screenshot. I have a WD NAS and a Buffalo Linkstation. Both do work under Windows just not longer under Ubuntu.

---

### Post by Paqman on 2011-05-22
How were you accessing your NAS? Do you have an entry in /etc/fstab that mounts it automatically, or do you just access it through a link in Nautilus?

You should need the whole Samba package installed to do either, by the way. Ubuntu comes with the Samba client packages installed by default, and that's all you need to access a remote machine with Windows shares on it.

---

### Post by gandaran on 2011-05-22
> **linux_believer said:**
> I somehow lost access to my NAS. I had samba installed previously and it just worked. Over a few months it worked fine then one day nothing. I thought with a fresh install it would correct the issue. Recently installed Natty and the problem still persist. Sometimes I cannot even see the NAS. See the attached screenshot. I have a WD NAS and a Buffalo Linkstation. Both do work under Windows just not longer under Ubuntu.
do you know the NAS share IP? it's something like this 
```
smb://192.168.0.1/share/
```
type the IP in the file browser url bar or local » connect to server » windows shares.
then bookmark the share in the file browser for future easy access.
theres no need to install samba for just accessing windows/NAS shares.

---

