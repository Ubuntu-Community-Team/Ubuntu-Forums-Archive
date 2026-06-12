---
title: "Streaming media to VLC on Fire stick with password protection"
date: 2020-05-07
forum: Networking &amp; Wireless
---

### Post by .Ricky. on 2020-05-07
Hello,

My aim is to stream my media content to my TV which has an Amazon Fire stick. On there, I use VLC. 

It used to work fine until the upgrade to Ubuntu 20.04: to make it work I was using samba, but system-config-samba has been removed a couple of distros ago and with 20.04 I now can't install it any longer.

The contents of smb.conf did not change, but now I can't access my content with VLC any longer. I think the issue lies with the fact that I want access to the shared folders to be password protected, only accessible by a specific user (therefore I am not using the Ubuntu option to share media through rygel, because there's no password protection).

nautilus-share isn't helping either.

I've read so many guides now on how to set up samba, but they all say the same thing and I always come to the same result: I can access public folders, but not those that require authentication.

What can I do?

---

### Post by SeijiSensei on 2020-05-07
Did you create samba users using the smbpasswd program?

```
sudo smbpasswd -a username
```

Pick a username that also exists on Linux.  Make sure that user has rights to the share.  In smb.conf
```

[sharename]
     path=/path/to/the/share
     browseable = yes
     guest ok = no
     writable = yes
     valid users = username

```
If you want the share owned by a "dummy" user with limited rights,  you can add the "force user" and "force group" parameters to smb.conf.  Then every file will be owned by the user referenced in the "force user" directive.

---

### Post by TheFu on 2020-05-07
VLC on android supports DLNA servers - View -> Playlists is where I think it was last time I looked.  
miniDLNA is pretty easy to setup.

---

### Post by ajgreeny on 2020-05-07
> **TheFu said:**
> VLC on android supports DLNA servers - View -> Playlists is where I think it was last time I looked.  
miniDLNA is pretty easy to setup.
Spot on! That is where it is, in the uPnp section I think; I used it myself until very recently, though have now started using emby mediaserver in its place, and as an alternative  to plex mediaserver.

Either of those would, I think, also work for you assuming there are client apps for emby and plex available for an Amazon fire stick.

---

