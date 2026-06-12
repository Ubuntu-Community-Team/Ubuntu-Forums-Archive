---
title: "[SOLVED] Nautilus won't list SMB shares"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by jinksys on 2008-08-19
I have an odd problem.  Nautilus will show my samba servers but when I click on them they won't have any shares.  It's odd because I can do a smbtree command and get:

```

WORKGROUP
	\\NAS            		Samba 3.0.28a
		\\NAS\core           	FILE SHARE
		\\NAS\IPC$           	IPC Service (Samba 3.0.28a)
	\\MASTER         		Samba 3.0.26a-3.7-1787-SUSE-SL10.3
		\\MASTER\IPC$           	IPC Service (Samba 3.0.26a-3.7-1787-SUSE-SL10.3)
		\\MASTER\core           	FILE SHARE

```

I can also use smbclient to connect as well, so I know samba is working on both my machine and my servers.

---

### Post by jerome1232 on 2008-08-19
I get that when the other computers are vista, but xp computers show up fine.

---

### Post by jinksys on 2008-08-19
> **jerome1232 said:**
> I get that when the other computers are vista, but xp computers show up fine.

All my systems are ubuntu 8.04.  I have two ubuntu samba servers, and my laptop which is having the nautilus problem.

---

### Post by dmizer on 2008-08-19
If all your systems are Ubuntu, you have lots of options.

First, take a look here: [http://ubuntuforums.org/showthread.php?t=702131](http://ubuntuforums.org/showthread.php?t=702131)

You will find that samba is lacking in many ways. If you find that you need something faster, and more reliable, take a look at NFS. There is a fantastic howto for NFS linked in my signature.

---

### Post by Alistair George on 2008-08-19
Funny I just posted similar. Nautilus or associate 'Connect to Server' is flakey try the Gnome Commander which works well.

[http://ubuntuforums.org/showthread.php?t=894892&highlight=nautilus](http://ubuntuforums.org/showthread.php?t=894892&highlight=nautilus)
[http://ubuntuforums.org/showthread.php?t=830032&highlight=couldn%27t+display+network%3A%2F%2F%2F&page=2](http://ubuntuforums.org/showthread.php?t=830032&highlight=couldn%27t+display+network%3A%2F%2F%2F&page=2)

What I've found is that with a relog on Ctrl-Alt-Backspace and same logon the shares become visible in Nautilus!!
Cheers,
Alistair.

---

### Post by motin on 2008-08-20
This is a bug: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/236903](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/236903)

Use smb4k or konqueror as a work around...

---

### Post by Alistair George on 2008-08-20
> **motin said:**
> This is a bug: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/236903](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/236903)

Use smb4k or konqueror as a work around...


OK thank you.

---

### Post by dmizer on 2008-08-20
You should be able to get Nautilus to browse windows shares.

I linked to the directions earlier, did they not work?  All you should need to do is install two things:
```
sudo aptitude install samba-client
```
```
sudo aptitude install libgnomevfs2-extra
```

---

### Post by Alistair George on 2008-08-20
> **dmizer said:**
> You should be able to get Nautilus to browse windows shares.

I linked to the directions earlier, did they not work?  All you should need to do is install two things:
```
sudo aptitude install samba-client
```
```
sudo aptitude install libgnomevfs2-extra
```

samba-client is same as smbclient isnt it? anyways, its recognised as a bug and I have both of those items above installed if smbclient is the same item.
Cheers,
Alistair.

---

### Post by jinksys on 2008-08-20
> **dmizer said:**
> You should be able to get Nautilus to browse windows shares.

I linked to the directions earlier, did they not work?  All you should need to do is install two things:
```
sudo aptitude install samba-client
```
```
sudo aptitude install libgnomevfs2-extra
```

What instructions? you told me that samba is borked and to use nfs.

---

### Post by jinksys on 2008-08-21
After checking Ubuntu Bugs, I noticed I wasn't the only one getting this problem.  I did find the reason Nautilus wasn't working, it is actually GVFS.  Here is my bug report and fix.

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/259978](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/259978)


Binary package hint: gvfs

I am using Ubuntu 8.04 with packages up to date.

My problem WAS that nautilus would list my Samba and Windows hosts, but when I clicked on them I wouldn't get any shares. I could use smbclient just fine, but gvfs-ls would timeout when trying to list samba shares, ie gvfs-ls smb://MASTER/core .

I fired up wireshark and noticed that whenever I used gvfs-ls smb:// that it sends out a DNS request to my ISP and gets back a successful lookup (wtf?) to 64.158.56.56. I use CHARTER COMMUNICATIONS and they resolve all bad lookups to their "helpful" search page, which explains why I get the timeouts.

I went to my /etc/samba/smb.conf file and uncommented and changed this line:

name resolve order = lmhosts host wins bcast
to
name resolve order = lmhosts wins bcast host

rebooted, and GVFS and Nautilus (as well as all GVFS enabled apps) were working like a dream.

---

### Post by Alistair George on 2008-08-21
Certainly got something there I didnt have to reboot it sorted it straight away - brilliant!

---

### Post by jinksys on 2008-08-21
> **Alistair George said:**
> Certainly got something there I didnt have to reboot it sorted it straight away - brilliant!

Glad this helped you.  Hopefully the Ubuntu team will take notice of my bug report and it'll help out others as well.

May I ask what internet provider you use and do they also provide the not so handy search page upon bad DNS requests?

---

### Post by dmizer on 2008-08-21
Would help if you linked to your bug.

This is actually expected behavior, but the problem is extremely simple to fix by changing the default smb.conf script.

The order that hosts are resolved in DOES make a difference.  On any computer (including Windows), if you try to resolve DNS before WINS or hosts, you will usually get a failure.

Good for you for figuring it out though.

---

### Post by Alistair George on 2008-08-23
Unfortunately, this has reverted back to not working despite the smb.conf being modified. First it worked as modified, now it does not; requires further investigation. Unfortunately, one cannot UNSOLVE a SOLVED thread.
Alistair.

---

### Post by dmizer on 2008-08-23
> **Alistair George said:**
> Unfortunately, this has reverted back to not working despite the smb.conf being modified. First it worked as modified, now it does not; requires further investigation. Unfortunately, one cannot UNSOLVE a SOLVED thread.
Alistair.
This is not your thread, so you cannot unsolve it. If jinksys is is still having an issue, jinksys is more than welcome to mark the thread as unsolved.

---

### Post by jinksys on 2008-08-23
> **Alistair George said:**
> Unfortunately, this has reverted back to not working despite the smb.conf being modified. First it worked as modified, now it does not; requires further investigation. Unfortunately, one cannot UNSOLVE a SOLVED thread.
Alistair.

That is interesting.  Could you go to the terminal and post the output of smbtree?

---

