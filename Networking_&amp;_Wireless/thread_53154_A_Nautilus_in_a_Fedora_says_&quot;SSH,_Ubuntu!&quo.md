---
title: "A Nautilus in a Fedora says &quot;SSH, Ubuntu!&quot;"
date: 2005-07-30
forum: Networking &amp; Wireless
---

### Post by geokker on 2005-07-30
The 'Connect to server...' menu item in the Gnome menu allows me to connect to another linux box via SFTP through SSH. To me this sounds ideal. Samba should be redundant if I'm in a room without Windows. 

I can open a folder ok but run into some problems when opening and saving files.

E.g. After dragging and dropping 'hotstuff.jpg' into:

```
sftp://SweatyLoveGod@10.0.6.66:22/var/images
```

I try to open it directly into the Gimp:

```
Opening '/home/SweatyLoveGod/sftp://SweatyLoveGod@10.0.6.66:22/var/images/crop.jpg' failed:

Plug-In could not open image
```

If I try to save anything to the remote folder, There is nothing to find in the file browser.

So, how do I transparently make a remote folder appear as a local folder using SSH?

---

### Post by kvidell on 2005-07-30
[QUOTE=geokker]The 'Connect to server...' menu item in the Gnome menu allows me to connect to another linux box via SFTP through SSH. To me this sounds ideal. Samba should be redundant if I'm in a room without Windows. 

I can open a folder ok but run into some problems when opening and saving files.

E.g. After dragging and dropping 'hotstuff.jpg' into:

```
sftp://SweatyLoveGod@10.0.6.66:22/var/images
```

I try to open it directly into the Gimp:

```
Opening '/home/SweatyLoveGod/sftp://SweatyLoveGod@10.0.6.66:22/var/images/crop.jpg' failed:

Plug-In could not open image
```

If I try to save anything to the remote folder, There is nothing to find in the file browser.

So, how do I transparently make a remote folder appear as a local folder using SSH?[/QUOTE]
 I personally don't know of a way you can do this... There's probably some -L trick you can use but I don't know what it would be.

You could however try doing that same open command without the /home/SweatyLoveGod/ infront....

Maybe you could encapsulate an NFS mount inside an SSH tunnel? That would probably do it. That would be a -L trick.

---

