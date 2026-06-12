---
title: "How do I network a Kubuntu 6.10 computer with a Windows XP professional computer?"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by TheBasilisk on 2006-12-25
I'm a bit of a Kubuntu noob. I have no clue how to change my workgroup name or even establish a network in the first place. I know that I'm supposed to use Samba, but I don't know any of the commands. I need to network my Kubuntu 6.10 computer to a Windows XP Professional computer to transfer some files. Someone please help!

---

### Post by jpkotta on 2006-12-25
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Note: it may be as simple as getting the location bar in Nautilus with CTRL-L, and then typing in smb://192.168.0.2 (or whatever the ip address of your Windows machine is).

I think Konquerer has smb support as well.  Also check out smbfs, this is a nice permanent solution.

---

