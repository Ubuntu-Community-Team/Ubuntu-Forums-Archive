---
title: "permissions with bash script"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by kevcoder on 2011-06-25
how do I run a bash script with my permissions.

each of the following lines at the cli runs fine but in the script it errors 

script
```

#!/bin/bash

clear

sourceFolder=/home/dev/Downloads/torrents
destFolder=/srv/samba/share/
defOwner="nobody"
defGroup="sambashare"

mv $sourceFolder $destFolder

```permissions
```

dev@kevcoder00:/srv/samba/share$ ls -ld ~/Downloads/torrents
[COLOR=Blue] drwxr-xr-x 2 dev dev 4096 2011-06-25 13:05 /home/dev/Downloads/torrents[/COLOR]
dev@kevcoder00:/srv/samba/share$ ls -ld /srv/samba/share/*
[COLOR=Blue] drwxrwxr-x 2 nobody sambashare_kid 4096 2011-06-25 14:31 /srv/samba/share/casey
drwxrwxr-x 8 nobody sambashare     4096 2011-06-25 14:28 /srv/samba/share/movies
drwxrwxr-x 5 nobody sambashare     4096 2011-06-25 13:58 /srv/samba/share/music
[/COLOR]dev@kevcoder00:/srv/samba/share$ groups
[COLOR=Blue] dev adm dialout cdrom sudo plugdev lpadmin admin sambashare sambashare_kid[/COLOR]

```the error
```

dev@kevcoder00:/srv/samba/share$ ~/scripts/move_torrents
[COLOR=Red] bash: /home/dev/scripts/move_torrents: Permission denied[/COLOR]

```

---

### Post by josephmills on 2011-06-25
```
sudo -s 
``` will drop you to root to get out of it do an ```
exit 
``` also see [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

you might have to chmod -x that torrent

---

### Post by furtypajohn on 2011-06-29
Make sure the script is executable.

```
chmod u+x ~/scripts/move_torrents
```

---

### Post by kevcoder on 2011-06-30
> **furtypajohn said:**
> Make sure the script is executable.

```
chmod u+x ~/scripts/move_torrents
```

I also had to do a chmod 775, which brings me to another question:

Where do I configure default permissions for newly created files/directories by user?

---

### Post by furtypajohn on 2011-06-30
Edit the /etc/profile file and change: "umask 022" to whatever permissions you want

---

