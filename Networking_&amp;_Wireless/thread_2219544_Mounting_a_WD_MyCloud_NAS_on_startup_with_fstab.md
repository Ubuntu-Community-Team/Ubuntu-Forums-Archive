---
title: "Mounting a WD MyCloud NAS on startup with fstab"
date: 2014-04-24
forum: Networking &amp; Wireless
---

### Post by dmorpher on 2014-04-24
Hello,

I am running Ubuntu 14.04 and I have a Western Digital MyCloud NAS connected to the router, and I tried to get it to mount at startup editing /etc/fstab . In my NAS I have two folders I want to mount, one public (named Public) and another one Private (named Safe).

First I tried to mount it with CIFS:

```
//192.168.1.99/Public /home/[my_user]/MyCloud/Public cifs credentials=/home/[my_user]/.creds,iocharset=utf8,sec=ntlm,gid=1000,uid=1000,file_mode=0775,dir_mode=0775 0 0

//192.168.1.99/Safe /home/[my_user]/MyCloud/Safe cifs credentials=/home/[my_user]/.creds,iocharset=utf8,sec=ntlm,gid=1000,uid=1000,file_mode=0775,dir_mode=0775 0 0
```

The problem I had with CIFS is that If I move a not-too-big file, like 300-400 MB, the speeds can go up to ~30MByte/s. If I want to move a ~1,6 GB file, the speed begins lower (~10MB/s) and drops to 800~900 KBytes/s after 20 or 30 seconds.

Someone told me I should try with NFS, which would improve transfer speeds, and it had the option of "hanging in there" if the wifi had a hiccup and resume after the connection is restablished. I enabled NFS on the MyCloud server, and this is what I got:

```
192.168.1.99:/nfs /home/oriolfm/MyCloud nfs rw,hard,intr 0 0
```

This code tried to mount both folders, Public and Safe, and got them displayed in my file manager as mounted, but I couldn't find the way of giving the NAS a username and Password with NFS, so I could acces the Public Folder but not the Safe one (I didn't get permission). Furthermore, If I tried to move some files from my computer to the Public folder, it would copy the first one, then the dialog would freeze and stop there.

What can I do to make it work?

Thank you.

---

### Post by Scooby-2 on 2014-08-05
This is an old thread but as it is unanswered maybe this will help someone.

I too have a My Cloud server on my network, for which I use NFS. NFS uses uid/gid for authority, and access is granted based on the UID of the owner of the files and the uid used in the client's mount command. Hence user names and passwords cannot be used over NFS. Get the id of the user on the client using the id command in the form id {username}, e.g.

> id kevin
uid=1005(kevin) gid=1000(kevin) groups=1000(kevin),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),110(sambashare),126(vboxusers)

then log in to the server, where you have previously created a user (in my case also kevin) from the My Cloud UI, and issue the same command:

> id kevin
uid=1000(kevin) gid=1000(share) groups=1000(share),33(www-data),1001(administrators)

Users are created on the My Cloud starting from 1000. Here you can see that the uid's don't match - I have a uid of  1005 on the client and 1000 on the server. If your uids match jump to the paragraph which starts with "We need to make a minor change..."  Otherwise, check to see if you have uid 1005 available on the server:

> getent passwd 1005


If it returns nothing, it's OK to use.** Change the uid of the user on the server:

> usermod -u 1005 kevin


We need to make a minor change to the way the filesystems are exported in NFS so that the uid is not transposed to that of the "anybody" user. On the server, copy and paste the following line:

> f="/etc/exports" && cp "$f" "${f}.bak" && sed -i "s/,all_squash,/,no_all_squash,/" "$f"


This creates a copy of the exports configuration file and then makes the necessary change to it.

Restart the NFS export on the server to take into account the change with:

> exportfs -a


Make the mount point on the client:

> mkdir ~/nas


Mount it on the client using udp and NFS version 3 (the server doesn't support V4, I'm afraid):

> sudo mount -o udp,vers=3,soft,intr,rsize=8192,wsize=8192 nas:/nfs /home/kevin/nas


Note 1: If you make changes to a user's access to various shares in the UI, this only affects users who connect via Samba, where a user name and password can be specified.
Note 2:WD does not support Linux despite the fact that this box runs Debian and exports the filesystems using NFS by default.

** If you find uid 1005 returns details of a user, choose a uid like 1100 and use the getent command to ensure it is available on both server and client. If the command returns nothing, that uid is unused.

---

### Post by Scooby-2 on 2014-08-05
P.S Your /etc/fstab entry would be:
> 192.168.1.99:/nfs /home/oriolfm/MyCloud nfs rw,udp,vers=3,soft,intr,rsize=8192,wsize=8192    0    0

---

### Post by jeb5 on 2014-11-09
I was following perfectly until you came to the part that says to log in to the MyCloud UI (the web UI?) and execute a command line command?????

I've been all through the settings and haven't seen any way to do that.  Are you referring to some kind of MyCloud desktop software for Ubuntu?  I've been googling how to setup MyCloud with NFS for several hours now, and it makes sense what you say about how the UID's have to match (thus no user/pass option can be used).  That all makes sense, but how to tap in to the MyCloud ... in that way ... I'm lost.

On my network setup, the MyCloud is stand-alone, not hooked up to a separate server PC where I can easily look up UID's.  My LAN is all Gigabit.

Would you mind explaining/clarifying that part for me?  I'm totally OK with command line, although I am learning Ubuntu/Linux command line from the ground up at the moment.  I just haven't found the correct commands to use yet, and I'm still getting comfortable with the huge amont of config files on Ubuntu.

NOTE:  I've successfully configured CIFS, and I was about to try samba, but saw several posts about it being buggy still on Ubuntu.  The only issue with CIFS is that I seem to be at a 10 MBps cap, while on windows I can get up to 80+ MBps transfer rate.  I'm just exploring options (NFS for now) to see how I can get comparable speeds in Ubuntu.  It's either a configuration thing, or a protocol thing.  Still not sure which yet.

---

### Post by Scooby-2 on 2014-11-09
> **jeb5 said:**
> I was following perfectly until you came to the part that says to log in to the MyCloud UI (the web UI?) and execute a command line command?????

@jeb5

What step are you at? Is it part 1 or 2? I must be going daft because I cannot find the text you are referring to even after searching both parts for "UI" and "command." :confused:

Scooby-2

---

### Post by jeb5 on 2014-11-09
My apologies, I guess that would have been step 2:

[QUOTE=Scooby-2]then log in to the server, where you have previously created a user (in  my case also kevin) from the My Cloud UI, and issue the same command:
[/QUOTE]

It's the "from the My Cloud UI" part that confuses me.  The only My Cloud UI that I know of is the Web Interface ([http://[ip_of_NAS]](http://[ip_of_NAS])), unless there's something totally different about My Cloud that I'm not aware of.  It seems like your setup is with the My Cloud hooked up as USB v3 to a server computer where user accounts and permissions can be set via command line?

My setup is different.  My "My Cloud" is simply on the network (hooked up via CAT5), and my only configuration resources (that I know of) are through the Web UI.

Did I miss something?

---

### Post by jeb5 on 2014-11-09
Ok my bad ... I just found your tutorial and the using SSH part is what I was missing.  My bad!  And thanks for posting that tutorial!

---

### Post by juhan2 on 2015-01-30
...using SSH part...

be aware of the "fine print" in WD documentation and/or user interface: you invalidate your warrantee by enabling ssh! To be fair to WD, getting "root" access to a device with embedded Linux is dangerous: you can really mess it up. However, we have to do what we have to do, but be careful. I would recommend checking out the device fully, with all other client machines (Mac, Windows, *nix, mobile, media players) using their standard functionality. If anything is broken, you might need to exchange the device. Once you're sure it's OK, you can then get more adventurous...

p.s. I'm using it mainly to replace the disk for TimeMachine backups of my Mac. I added Windows backup. I checked out iPad mini access. I'm playing with Ubuntu access. So far, so good (nothing fancy). Big surprise (didn't expect it) Ubuntu banshee media player can play DAAP server contents that I loaded from iTunes (on Windows, didn't want to risk Mac). Looks like Apple did remove their DRM protections! That's great! I'm jazzed (heh)!

---

### Post by jeb5 on 2016-01-08
@ Scooby-2

Man, I've done a LOT of tinkering since I last posted here.  Just want to say that I did manage to successfully downgrade the firmware, and I've learned a LOT more about *NIX systems since then.  My previous comment about having a "different setup" was a very noob thing to say for sure.

I now have much better understanding of how users, groups, IDs for both, and file/folder permissions all play together with NFS and SMB.  Now I'm at the point where I need to basically create new folders with appropriate permissions and move my content to that folder so I can use it :-P ... or at least that's one way of doing it.  I'm still weighing many factors, such as security (darn NFS).

Thanks again to the posters in this thread!  You guys got me started on the right path for sure!

---

### Post by Scooby-2 on 2016-01-09
[COLOR=#000000]@jeb5

I'm glad this helped and thanks for the feedback. It's all about passing information on and learning.

:D[/COLOR]

---

