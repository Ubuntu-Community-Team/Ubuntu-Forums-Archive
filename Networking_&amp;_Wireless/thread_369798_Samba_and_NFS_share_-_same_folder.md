---
title: "Samba and NFS share - same folder"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by HereInOz on 2007-02-25
A simple question as to whether it is OK to set up the same folder;ie, /home/username as both a Samba share and an NFS share.  

I did this once before and at about the same time, my Samba installation went belly up, and was not able (by me, anyway) to be recovered.  Are there any issues regarding the setting up of one folder as both a Samba and NFS share, or was my previous experience purely coincidental.

If you have any experience in this area, it would be great to hear from you.

Cheers,

Alan

---

### Post by kidders on 2007-02-25
Hi there,

You can share & re-share the same things over and over, as much as you like.

The only side-effect of doing so is that, by providing more than one distinct means of accessing a file, you increase the probability of odd things happening, should multiple simultaneous (or nearly simultaneous) modifications take place. You won't cause any *damage*, but you may notice odd behaviour.

If that caveat doesn't apply to you, I can't think of any reason to be concerned.

I hope that helps.

---

### Post by dmizer on 2007-02-25
i have read many times of people having problems with this configuration.  i don't have many windows computers so i don't use samba often except at work.  and even though the file server at work is an ubuntu samba server, i still connect to it using samba instead of nfs because that's what everyone uses.  and the shares are too sensitive for me to risk the nfs setup as well.

i suspect the problem would occur if both a samba connection and an nfs connection were active and writing at the same time.  this may cause a directory corruption or similar.

on my home server, i host out my entire home directory with nfs, and restrict samba to a folder within the user directory, and i haven't experienced any problems using either my nfs connection, or my samba connection via my windows virtual machine.

further, i think there should be no problem if either nfs or samba were hosted out as read only.

i don't have gobs of experience with this so take it with a grain of salt, but i do suggest caution.

---

### Post by kidders on 2007-02-25
Hi dmizer,

> **dmizer said:**
> i suspect the problem would occur if both a samba connection and an nfs connection were active and writing at the same time.  this may cause a directory corruption or similar.The Linux kernel would still be the thing in control of what's getting written. From its perspective, sharing a file over Samba & NFS would be no different than opening a file in gedit and kate & saving it with both applications at the same time. If there was even a *small* chance that doing that could cause a directory to corrupt, Linux would be totally unusable! Having said that, you can be 100% certain that the wrong thing (from one editor's perspective) will end up in the file!

The kind of scenario you described *could* cause weird client-side behaviour though. For instance, Samba might suddenly lose a lock on a file that it expected to be able to keep, resulting in some sort of "Access denied" error, that would go away again, moments later. Also, if one sharing service held onto locks longer than it perhaps should, the other could conceivably hang for a moment, while it waited for them to release.

I'd say a server would need to be subjected to some pretty heavy use to provoke any of these sorts of things though. Operating systems are pretty good at handling simultaneous access to the same resource by multiple processes. The fact that those processes might be sharing things over a network isn't terribly important.

---

### Post by HereInOz on 2007-02-25
Thanks good people.  I will take all that on board and might try it on another installation about which I don't care a great deal, and which I don't mind if it falls over, rather than test it out first on my main file server.

---

