---
title: "[SOLVED] Adding a network drive from a ubuntu server (avoiding samba)"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by OverlordManny on 2008-11-27
Hello,

Here's my set-up I'm running Ubuntu 8.10 desktop as a small file server. I'm using the same OS on my desktop machine and laptop. I want to mount a folder from my server to my desktop machine. I want to avoid using samba because winbind is conflicting with firefox3 making it unusable. Is there another way? I have absolutely no Microsoft OS's on this network. Is Samba really needed in this case? I would like to have the network folder auto-mount at start-up. I had all of this working when my server was running WinXP using cifs but due to the wimbind/firefox3 conflict I decided to use Ubuntu on my server trying to avoid winbind. If you con point me to a useful thread or help in anyway I'd appreciate it. Any time I search for this all I seem to find is samba guides.

---

### Post by adaptr on 2008-11-27
On the machine you want to share a folder:
```
apt-get install nfs-kernel-server
nano -w /etc/exports
[COLOR=Blue]ADD this: >>[/COLOR] /dir/to/share *(rw)
exportfs
```On the machine you want to mount it:
```
apt-get install nfs-client
nano -w /etc/fstab
[COLOR=Blue]ADD this: >>[/COLOR] servername:/dir/to/share /mount/point nfs auto 0 0
mount -a
```

---

### Post by OverlordManny on 2008-11-27
Ok I had tried this before but I kept on getting:

mount.nfs: can't get address for //home-server

I also tried without the "//" and I tried using the IP directly but still no go! Any more advice friend?

---

### Post by OverlordManny on 2008-11-27
Ok I got it I had to add my servers ip to /etc/hosts. Now it's like butter. Though oddly enough Nautilus tells me that the files are on a video dvd and asks if I want to play them lol.

---

