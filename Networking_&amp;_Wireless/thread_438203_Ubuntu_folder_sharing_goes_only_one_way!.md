---
title: "Ubuntu folder sharing goes only one way!"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by superyounan1 on 2007-05-09
I followed these instructions:
[http://www.ubuntuguide.org/]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read")

i can mount my windows folders very nicely, but I cant mount folders from my other ubuntu machine.

This is my fstab entry:
```

//192.168.1.101/Videos    /media/younan_videos smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

```

and my username and password in the smbcredentials file are correct.

to verify that the network path is correct, I entered it into nautilus and was able to browse the directory correctly.

```

sudo mount -a
31889: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

```

does anyone know how to fix this?:confused:

---

### Post by superyounan1 on 2007-05-09
anyone mounting from ubuntu to ubuntu over network?

---

