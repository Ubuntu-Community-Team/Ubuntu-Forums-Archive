---
title: "Samba Problems...."
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by tom-ubuntu on 2008-06-28
Dear all,

Hardy is giving me a hard time with Samba....

Since the last update I am experience even bigger problems with Samba then ever. 

My video and music collecton is on a NAS device (Synology), providing samba shares. Every correctly setup, as with other clients accessing them is no problem. Well, nothing changed in the last few weeks/months anyway. Working fine.

Now I can not even view a video with Totem from the share. Giving me 

```
An error occurred: 
Could not read from ressource". 
```

Update: Starting totem with terminal and drag'n drop a file from the share gives the following error:

```
** Message: Error: Could not read from resource.
gstgnomevfssrc.c(683): gst_gnome_vfs_src_create (): /play/source:
Failed to read data: Invalid parameters
```


Or Rhythmbox just stops in the middle of a track, trying to jump to the next, and then crash after a few tries to go to the next track. Starting Rhythmbox from the terminal, I receive the following error messages:

```
connection_message_func(): Callback
CALLBACK: fill-authentication!!!
```

Password to the share is stored in the keyring.

Something seems really wrong here.... 
As said, worked before...

Any ideas, please? Any help is very much appreciated.

Thanks,
Tom

---

### Post by tom-ubuntu on 2008-06-29
Ok, my GF machines is showing exactly the same problem. Worked fine before aswell....

Any tips?

---

### Post by tom-ubuntu on 2008-07-01
Today's update fixed the problem. 

Many thanks to the devs.

Cheers

---

### Post by Mountaineer on 2008-07-01
I was just looking for the solution to this problem that has been bugging me for weeks and I read that it has been fixed.  Sure enough it has.
My thanks to the devs too. :)

---

