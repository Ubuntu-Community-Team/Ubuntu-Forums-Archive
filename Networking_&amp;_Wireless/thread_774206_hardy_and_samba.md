---
title: "hardy and samba"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by jtravnick on 2008-04-29
Hi. I have a samba problem. samba is set to security share, folder /home/jim has read and write permissions in samba, but writing is restricted through fs for all folders under /home/jim/ except /home/jim/public which is 777. windows can write to this folder, but other linux computers can neither write to the folder  or see the files written to this folder by the windows computer. I am also attaching my samba file

jim@jim-desktop:~$ ls -la /home/jim/public
total 12
drwxrwxrwx  3 jim    jim     4096 2008-04-29 08:43 .
drwxr-xr-x 47 jim    jim     4096 2008-04-29 09:05 ..
drwxrwxrwx  2 nobody nogroup 4096 2008-04-29 08:43 Test
jim@jim-desktop:~$ 

## samba configuration file
#
# remember to set /home/"user_name" correctly
# if you want to add more shares, just copy share nr 1 and add it beneath
# This is insecure.

[global] workgroup = "mshome"
server string = Samba Server
security = share
name resolve order = lmhosts hosts

[nameofshare]
path = /home/jim/
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

Any help would be appreciated  think lassegul must have spent 3 hours on irc trying to help get this up. Think were very close just not there yet.

Jim

---

### Post by Iowan on 2008-04-29
May not matter, but did you uncomment the **guest account = nobody** line?

---

### Post by lassegs on 2008-04-30
> **Iowan said:**
> May not matter, but did you uncomment the **guest account = nobody** line?

This is the entire smb.conf
```

[global] workgroup = "mshome"
server string = Samba Server
security = share
name resolve order = lmhosts hosts

[nameofshare]
path = /home/jim/
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

```

---

### Post by jtravnick on 2008-04-30
Made a couple of changes to the file nothing major it now reads:

```
## samba configuration file
#
# remember to set /home/"user_name" correctly
# if you want to add more shares, just copy share nr 1 and add it beneath
# This is insecure.

[global] 
workgroup = MSHOME
server string = Samba Server
security = share
name resolve order = lmhosts hosts

[jim-desktop]
path = /home/jim/
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

```

The only thing this did was make it easer for me to find when I pull up networks. Though it does seem to take a long time to load when I boot the system before I am able to see the desktop.

Also I am now wondering if I should just do the sharing when all systems are in linux differently. I booted this desktop to fedora to see how I had that set up. It does SFTP and works perfect the laptop can see it right away and can write to it. So now I'm wondering if maybe thats how I should set up the Ubuntu boot on both the desktop and laptop.

Only problem I dont remember how I set it up in fedora or if the steps are the same.

This is starting to get real frustrating for me and making me wonder why I even upgraded to hardy since everything worked in gutsy and really did not have any complaints with it.

Jim

---

