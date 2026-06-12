---
title: "Ubuntu Network"
date: 2017-12-18
forum: Networking &amp; Wireless
---

### Post by jbamford92 on 2017-12-18
Howdy folks,

Ive recently switched to Ubuntu from macOS. Heres a quick question. 

I have a Server running FreeNAS connecting via SMB/SAMBA. However are there any tweaks to do in Ubuntu to get faster speeds accross the network? Reasons why im asking is because in Windows 10 i get 130megs accross the network however in Ubuntu im only limited to 60megs. I have a main feed from my HP Procurve gigabit switch ive tried jumbo frames in Linux but only seem to get 60megs still. 

Another issue i have is when listening to music in Linux when i access my Server the Music stops until everything on the server is loaded. The Music is also on my Server.

Any ideas? 

Thank you.

Jack.

---

### Post by TheFu on 2017-12-19
Don't use samba/CIFS for file sharing under Unix systems. Use NFS. That is the native network file system for all Unix-like OSes.  You can run both samba and nfs to access the same storage, BTW.

BTW, the specific HW involved in all aspects of the file transfers will matter.  130Mbps is pretty fast for spinning disks.  After the disk buffers (RAM) are filled, I'd expect the performance to drop to 65Mbps or so.  Linux automatically uses whatever RAM is left for network and disk buffering. You can watch that with the 'free' command.

nfs has lower overhead than CIFS, so a 10% performance improvement is common just by that switch.  NFS can be tuned for greater performance or to support thousands of clients.  For a small number of nfs clients, the tuning generally isn't needed.

---

### Post by jbamford92 on 2017-12-19
> **TheFu said:**
> Don't use samba/CIFS for file sharing under Unix systems. Use NFS. That is the native network file system for all Unix-like OSes.  You can run both samba and nfs to access the same storage, BTW.

BTW, the specific HW involved in all aspects of the file transfers will matter.  130Mbps is pretty fast for spinning disks.  After the disk buffers (RAM) are filled, I'd expect the performance to drop to 65Mbps or so.  Linux automatically uses whatever RAM is left for network and disk buffering. You can watch that with the 'free' command.

nfs has lower overhead than CIFS, so a 10% performance improvement is common just by that switch.  NFS can be tuned for greater performance or to support thousands of clients.  For a small number of nfs clients, the tuning generally isn't needed.

Cheers for your reply. I believe i need to install NFS? NFS is enabled in FreeNAS but doesnt show NFS share under Network Section in Files. I guess this will work? 
[COLOR=#3A3A3A]
sudo apt-get update

[/COLOR][COLOR=#3A3A3A]sudo apt-get install nfs-kernel-server

Thanks. 

Jack.[/COLOR]

---

### Post by slickymaster on 2017-12-19
Thread moved to **Networking & Wireless** for a better fit

---

### Post by TheFu on 2017-12-19
I don't know anything about FreeNAS - prefer my file servers to be setup **my** way, not someone else's.

As for NFS - there is a server and a client. Each will need to be configured correctly. The main differences to what you may have used previously is that
* NFS is server to server, not userid to server storage.  
* File permissions are Unix.  That means that uids and gids must match between systems for those to work correctly.  Use the 'id' command to see the numbers for each username you want to have access or share files.
* A basic understanding of Unix directory and file permissions is required.  This isn't an NFS thing, but it is a Unix or Linux thing.  NFS permissions are the same and translate 99%.

There are nfs how-to guides all over the internet.  Best to use Ubuntu.com or help.ubuntu.com data as the primary sources, since those will be release specific.  NFS doesn't care if you run Ubuntu Server or any of the ubuntu desktops.  It doesn't work at any GUI layer. It is all config files and restarting daemons stuff.  There isn't an NFS GUI.  Properly configured NFS storage appears like local storage to all programs.  'nfs-kernel-server' isn't needed on the "client", which I'm guessing is your Ubuntu system.

---

### Post by Morbius1 on 2017-12-19
If your FreeNAS is using a version of Samba that is relatively recent it can use SMB-Version 3 of the dialect. A Linux client - if you are using a file manager - uses SMB-Version 1.

You can do a quick thing to see if that will make a difference in your situation.

On Ubuntu:

Edit /etc/samba/smb.conf
Right under the workgroup = WORKGROUP line add this one:
```
client max protocol = SMB3
```
Note: setting the max protocol to SMB3 messes up host browsing - it's a Linux thing - so you have to access the NAS by name explicitly,

---

### Post by jbamford92 on 2017-12-20
> **Morbius1 said:**
> If your FreeNAS is using a version of Samba that is relatively recent it can use SMB-Version 3 of the dialect. A Linux client - if you are using a file manager - uses SMB-Version 1.

You can do a quick thing to see if that will make a difference in your situation.

On Ubuntu:

Edit /etc/samba/smb.conf
Right under the workgroup = WORKGROUP line add this one:
```
client max protocol = SMB3
```
Note: setting the max protocol to SMB3 messes up host browsing - it's a Linux thing - so you have to access the NAS by name explicitly,

Ive done that. Shares now loads faster. I installed a Networking Utility tool reporting to be just under 500megs. I do have Dual Lans in Round-Robin Mode on both machines.

Thanks for your help :).

---

