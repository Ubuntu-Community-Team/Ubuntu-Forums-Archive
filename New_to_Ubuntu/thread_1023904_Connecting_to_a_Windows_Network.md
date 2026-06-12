---
title: "Connecting to a Windows Network"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Woofsie on 2008-12-28
I'm using ubuntu 8.10 on my laptop and I can't connect to a pc running xp. My internet works fine, I have samba and smb4k installed. When I try to connect it says it failed to mount windows drive.

Apparently samba doesn't work if the windows machine has no password? I've put a password on my account, though there are other accounts on there with no password. Does it need to be a password on the workgroup or network?

The strange thing is, I could access the network the first day I had ubuntu installed, it didn't even take any configuration. It hasn't been working since then and I can't think of anything that has changed. :/

Any ideas?

---

### Post by Peter09 on 2008-12-28
It may already be mounted. I get a similar error if I try to mount a windows share (just by clicking on the icon in Nautilus). Have a look in the samba4k directory for the mount point.

---

### Post by mapes12 on 2008-12-28
This may help: [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

---

### Post by Joao Paz on 2008-12-28
Here's how I'm doing it - maybe there's a better way, but...

Local / Connect to server / Windows share /
On the Server field I set the IP of my Windows PC. Ex: 192.168.1.7 (I have static IPs on my home computers)
On the folder field I set the name of a shared folder. Ex: Public/ (always followed by the "/" character

I then bookmark it for later access.

If there's a better way, I'll be glad to try it :)

Hope it helps!

---

### Post by chrisod on 2008-12-28
Is the XP firewall blocking you? I've had it magically reset itself to block LAN access after a Windows update.

---

