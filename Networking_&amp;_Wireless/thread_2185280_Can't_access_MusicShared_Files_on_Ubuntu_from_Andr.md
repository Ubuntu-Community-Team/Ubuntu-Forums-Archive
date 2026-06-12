---
title: "Can't access Music/Shared Files on Ubuntu from Android/Windows"
date: 2013-11-01
forum: Networking &amp; Wireless
---

### Post by khan.orak on 2013-11-01
Hello great community,

I think I have had enough of information but to be honest, I understood none about editing smb.conf and making changes to Samba permissions or Linux permissions.

Now I have come to seek experts' opinion. My scenario is pretty simple.

I have two folders to share.

1. ~/Music/ which is created by Ubuntu installation. I have created various folders and files inside Music folder. I want to share this folder but with READ-ONLY access so that I can just listen to music on my Windows/Android devices. 

I have already tried using Share Options and then ticking Share and Guest Access. The Folder with its structure appears but I can't access it.

2. ~/Videos/Movies I have created this folder myself. I have shared this folder by Right-Click --> Properties --> Share method and have checked Guest Access. It works fine and I can access the files. I don't know why

Any help would be appreciated.

---

### Post by tgalati4 on 2013-11-01
Open a terminal:

```
cd
ls -la
```

Just cut and paste the /Music line.

Compare it to the /Videos/Movies line.

You shouldn't have to modify smb.conf unless there is a sharing option that is not available in Nautilus or you have a special share situation.

Try undoing any changes that you made to smb.conf.  If you did make changes, you need to restart the SAMBA server:

```
sudo service samba restart
```

---

### Post by khan.orak on 2013-11-01
> **tgalati4 said:**
> Open a terminal:

```
cd
ls -la
```

Just cut and paste the /Music line.

Compare it to the /Videos/Movies line.

You shouldn't have to modify smb.conf unless there is a sharing option that is not available in Nautilus or you have a special share situation.

Try undoing any changes that you made to smb.conf.  If you did make changes, you need to restart the SAMBA server:

```
sudo service samba restart
```

Thanks for the reply.

The VIDEOS folder which can be accessed, has the following line:
```
drwxr-xr-x  5 khanorak khanorak  4096 Oct 31 02:27 Videos
```

The Music folder has the following line:
```
drwxr-xr-x  6 khanorak khanorak  4096 Oct 27 15:25 Music
```

what does it show?

_**Edit:**_ Also restored the original smb.conf file. Restart smbd/nmbd services. Shared Music folder from Nautilus with guest access, but still not accessible on my Tablet. :(
[COLOR=#0000ff]
_**Edit 2:**_[/COLOR] I think I got it. I have to change permissions for the files and folders inside these two folders. I'll report back. Thanks for the headsup

---

