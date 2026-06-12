---
title: "setting up small home network"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by satipera on 2008-05-31
I have 2 ubuntu pc's at home which both access a wireless router. How do I set up a home network so I can access one pc desktop from the other and transfer files? ty.

---

### Post by dmizer on 2008-05-31
please see the fourth link in my signature regarding nfs shares.  the howto is short and gives directions for both server and client.

if you want to share files from both computers so that both computers can view and share eachothers files, you will need to configure each computer as both a server and a client.

---

### Post by Aearenda on 2008-05-31
I would just install nautilus-share in Synaptic and then right-click on the folder I wanted to share in Nautilus, and choose 'Sharing Options'. It uses Samba, so install samba from Synaptic too if not already present. The other computer can access the share from Places->Network. This inter-works with Windows computers too.

EDIT: You might have to log off and on again after installing nautilus-share before being able to create the first share.

---

### Post by dmizer on 2008-05-31
> **Aearenda said:**
> I would just install nautilus-share in Synaptic and then right-click on the folder I wanted to share in Nautilus, and choose 'Sharing Options'. It uses Samba, so install samba from Synaptic too if not already present. The other computer can access the share from Places->Network. This inter-works with Windows computers too.

EDIT: You might have to log off and on again after installing nautilus-share before being able to create the first share.

but ... this solution uses samba.  an unstable and slower protocol which is designed for windows, and backwards engineered to work on linux.  samba can be quite complex to configure.  and finally, sharing and mounting shares via nautilus means that many popular programs (azureus, rhythmbox, vlc, and more) will not be able to access the share. whereas nfs as configured according to the howto in my sig is easily accomplished in a matter of minutes.

of course, the main thing is that it solves your problem of sharing files satisfactorily. so either way is acceptable with that in mind.

---

### Post by satipera on 2008-06-01
Thanks I am going to have a go now, I will repost if I have problems.

---

### Post by josir on 2008-06-02
Hi, the fastest solution is to use NFS. I also agree that Samba is not a good solution because it's much slower and more difficult to configure than NFS.

I setup my 3-computers home network in 1 hour. I centralize my kids' mp3 files on one server and they now can listen and share their musics.

They stop fighting - until now :)))

Good Luck,
Josir.

---

