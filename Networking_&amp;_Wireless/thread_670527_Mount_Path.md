---
title: "Mount Path"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by creeva on 2008-01-17
OK this scenario is annoying me since I feel I'm missing something really stupid.

The scenario I'm attempting to rsync from my gutsy laptop to a smb share on a windows box.

I have the server mounted on my desktop - can I use this mount point and if so what is the path to get to these mounts. 

If not I'll mount it a second time via smbfs I'm just not sure if I really need to. 


Second what is the easiest way to setup a cron task for the rsync to take place. 



Sorry for the question that makes me feel like an idiot for asking but I've been trying to find the path for my desktop mount point  for a few hours.

---

### Post by tech9 on 2008-01-17
you could try mounting your samba share this way....

```

sudo mkdir /mnt/backup 
sudo mount -t cifs -o username="your_user_name"@"your_domain",password="your_password" //"your windows IP address"/"samba share" /mnt/backup

```then try to rsync... this should work

---

