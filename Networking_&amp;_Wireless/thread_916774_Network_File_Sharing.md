---
title: "Network File Sharing"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by [z]er0 HP on 2008-09-11
Hi,
I'm running hardy and i'm having trouble setting up a network for file sharing to my windows pc. I have had a quick fiddle with samba with no success. I want to be able to share my Music folder to my other computer. Windows computer is currently setup to share it's C drive, printers etc and is on workgroup "MSHOME" with computer name "user". ubunu pc is setup with computer name "ralphi" no idea how to set the workgroup.

Could you set me in the right direction please.
Thanks in advance

---

### Post by qstraza on 2008-09-11
to change work group, edit the /etc/samba/smb.conf
my line looks like this```
workgroup = MSHOME
```

Also put the following lines into smb.conf to share your dir
```

[share]
  comment = mp3s
  path = /home/localuser/mp3
  guest ok = yes
  read only = no
  create mask = 0777
  directory mask = 0777
  force user = localuser
  force group = localuser

```

Ofcourse, edit so it will suit your needs.
Hope this helps.

Also dont forget to reload your samba after editing```
sudo /etc/init.d/samba restart
```

---

### Post by superprash2003 on 2008-09-11
samba guide :[http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

