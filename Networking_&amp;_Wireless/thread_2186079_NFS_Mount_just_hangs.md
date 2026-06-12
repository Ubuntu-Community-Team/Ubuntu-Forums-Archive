---
title: "NFS Mount just hangs"
date: 2013-11-05
forum: Networking &amp; Wireless
---

### Post by ylafont on 2013-11-05
I am trying to mount an NFS share -  on a remote client, When i issue the command  the client just sit there and doen nothing. 

sudo mount -t nfs4 192.168.1.2:/srv/pxeboot/Images/knoppix /mnt/1
sudo mount -o soft,intr,rsize=8192,wsize=8192 192.168.1.2:/srv/pxeboot/Images/knoppix /mnt/1

showmount displays the correct share listing on the server. 

showmount -e 192.168.1.2
Export list for 192.168.1.2:
/srv/pxeboot/Images/knoppix 192.168.1.2
/srv/pxeboot                192.168.1.2

anyone  know?

---

### Post by ylafont on 2013-11-05
This seems to be a bug. 

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1247850](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1247850)

unless anyone has some ideas

---

### Post by the_master on 2014-03-16
I'm getting the same problem but i'm not running 13.10.  Both the server and client are running 12.04.  When i try and manually mount i don't get any errors in the syslog like the bug report says.

The odd thing is that i have other computers also running 12.04 that can mount everything fine.

---

### Post by nsk7even on 2014-03-27
I had this issue for a (semi-important) mount a few days now after installing new discs and configuring new raid/partitions etc. on my server. All other mounts worked well. But the problematic mountpoint keeps letting my client hang at calling the mount command. This issue persisted over days.
Now ... I restarted nfs-kernel-server at the server ... and it works again!

Sadly I did not checked whether it would have been worked from another client and I did not checked the showmount -e output.

I just wanna dump this into here if there are others than me out there that need some time until they get the idea to restart the nfs service :D :D

---

