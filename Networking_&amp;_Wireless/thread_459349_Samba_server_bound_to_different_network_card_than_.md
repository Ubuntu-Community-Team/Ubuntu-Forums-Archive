---
title: "Samba server bound to different network card than smbfs?"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by Wutzl on 2007-05-30
Hi,

in my setup, my 7.10 box needs to connect to a fileserver on my LAN (running under WinXP) - I  permanently mounted the fileserver using cifs in /etc/fstab.

On my 7.10 box there is also a WinXP install running under VMware server. I would like to share folders between my 7.10 box (the VMware host) and the local WinXP install (the VMware guest). I don't want to route this through my LAN for security and speed reasons. So my VMware server has two virtual network devices - one bridge to the LAN and one virtual private network with the host.

Now I would like to share a few folders on my 7.10 box with the VMware host through the private VMware network (i.e. I would like to restrict the samba SERVER to the private VM-interface, while using the other (physical)  interface to connect to my lan-fileserver with the samba CLIENT (cifs).

Now I have to problems:
1) If I restrict samba in smb.conf to the private interface, I can no longer mount the fileserver shares on the LAN through cifs in /etc/fstab (no route to host).

2) I set up samba in nautilus by rightclicking-share folder. When I now try to map the shared folder in the VMware XP guest, a user/password dialog pops up and doesn't accept the 7.10 user credentials.

Anyone knows how to fix this? Thanks!

---

