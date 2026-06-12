---
title: "[ubuntu] Xubuntu v16.04LTS: NFS config: client's fstab, mounting shares"
date: 2017-09-17
forum: Networking &amp; Wireless
---

### Post by kirbo719 on 2017-09-17
Recently deployed NFS server and client. Server and client machines run Xubuntu LTS v16.04.

Server is main desktop machine; client is a laptop usually -but not always - on the home LAN.

From the laptop client  /etc/fstab file I've included the pertinent mounts:

192.168.1.22:/home/bob /media/opti960/bob         nfs4 rsize=8192,wsize=8192,_netdev,nofail,intr  0  0
192.168.1.22:/mnt/backup /media/opti960/backup nfs4 rsize=8192,wsize=8192,_netdev,nofail,intr  0  0

note variables "_netdev" and "nofail"


It seems after deploying NFS, boot-time on the client is much longer, maybe 3x longer. I assume this is because fstab must wait for networking to start before it can complete its work. I hoped inclusion of "_netdev" would speed system boot, but I don't believe it has.

I included "nofail" so that when I use the laptop away from the home network, I will not obtain an error message complaining that the server shares couldn't be mounted.

MY QUESTIONS: Is my rationale correct using those variables? Is there a more elegant way to achieve satisfactory and swift boot when the server's shares aren't available to mount at the client?


MORE GENERALLY:
I changed from a Mint/Xfce distro on these machines weeks ago to Xubuntu/Xfce 64-bit, and it seems on the laptop that boot takes much, much longer than various distros of Ubuntu, Xubuntu and Mint I've used over the past couple years. Others have a similar experience?

On the laptop at boot, I get a message I don't recall seeing with other distros: "dev/sda2 clean." Dev/sda2 is the boot partition. The message leads me to believe the bootstrap process is error-checking sda2. Is that correct? Does the boot partition normally get error-checked each boot - or am I likely experiencing a hard disk issue?

Thank you in advance.

Bob

---

### Post by TheFu on 2017-09-19
To avoid the issues you are seeing, use **autofs** to mount the NFS storage, not the fstab.  Then it is only mounted when specifically accessed.

The config files are /etc/auto.master, /etc/auto.nfs

BTW, I think it is a very bad idea to use /media for NFS mount points.  That directory structure is managed by the OS temporary mount scripts. Best to avoid them.  Also, I'd use a generic HOME directory mount for NFS, not a specific one.

Backups really shouldn't be mounted all the time. That is a huge security issue with the viruses that like to encrypt storage.  Using a client/server backup method would be advised - duplicity, rdiff-backup, whatever ... anything that doesn't rely on the backup storage appearing as local.

And please when posting config files or cmd outputs, use "code tags" - that is available in Adv Reply (#) - or just wrap the stuff in [ code ] tags. I Usually use quote tags, then replace "quote" with "code" between the brackets.  Much more readable that way.

---

### Post by kirbo719 on 2017-09-23
Thanks for these ideas!

---

