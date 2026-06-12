---
title: "Need help setting up raspberry pi3 as NFS server - xubuntu client. errors"
date: 2016-03-07
forum: Networking &amp; Wireless
---

### Post by dan220 on 2016-03-07
have gone through obvious setup for debian of NFS server

clean install of raspibian .. raspberry pi 3

no firewall 

sudo apt-get install nfs-kernel-server nfs-common portmap

/etc/exports is set up as:

/home/pi 192.168.1.66(rw,sync,no_subtree_check)

to export the home directory to the named client (just made me think, maybe you can't export the home directory)

restarted kernel server to load export settings
(sudo /etc/init.d/nfs-kernel-server restart)

then, simply, as the debian NFS setup documentation states, and any current working NFS I already had

mount command =

sudo mount 192.168.1.64:/home/pi /home/user/m 

ip address of server - identifies the directory (what is in exports on the server) and the mount point

what I get is

mount: wrong fs type, bad option, bad superblock on 192.168.1.64:/home/pi,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

client is xubuntu

.......... was looking at portmap 

[http://www.cyberciti.biz/faq/missing-co ... her-error/]("http://www.cyberciti.biz/faq/missing-codepage-helper-program-other-error/")

I have NFS shares working -- xubuntu to xubuntu
The setup is the same as above

---

### Post by dan220 on 2016-03-07
seems to be fixed 

re thread on raspberry pi forum (by OP)

---

