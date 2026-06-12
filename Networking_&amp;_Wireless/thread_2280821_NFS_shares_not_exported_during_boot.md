---
title: "NFS shares not exported during boot"
date: 2015-06-02
forum: Networking &amp; Wireless
---

### Post by redrumrogue on 2015-06-02
I have started using NFS to share folders between ubuntu machines  running on my home network. I have one issue though which is that every  time I reboot the NFS server I have to manually run the command ```
sudo exportfs -arv
```  before the NFS clients can reconnect to the NFS share. Is the NFS  server supposed to automatically export the shares during boot? If not  then how can I get the server to do this?

All machines using NFS are running 14.04.2.

---

### Post by TheFu on 2015-06-02
Can you please post the /etc/exports file and permissions? Please use "code tags" so things line up.

---

### Post by redrumrogue on 2015-06-02
This is my /etc/exports file ...
```

# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

/home/justin/Videos/Downloads raspbmc(all_squash,no_subtree_check) inspiron(all_squash,no_subtree_check)

/home/justin/Music raspbmc(all_squash,no_subtree_check) inspiron(all_squash,no_subtree_check)

/home/justin/Dropbox/Photos raspbmc(all_squash,no_subtree_check) inspiron(all_squash,no_subtree_check)

/home/justin/Documents/VMHostShare 192.168.122.0/24(rw,async,all_squash,anonuid=1000,anongid=1000)

```

---

### Post by TheFu on 2015-06-02
Can you ping the client machines by those names?  raspbmc, inspiron?
Are the necessary NFS ports open on the clients AND on the server?

I never share stuff from under /home - NEVER. Don't recall why, but I suppose it was learned the hard way back in the 1990s.

---

### Post by redrumrogue on 2015-06-04
Yes from the server (IXTREME) I can ping RASPBMC by name.  INSPIRON is a windows laptop that's on and off all the time but i can ping by name when it's on.  Maybe it's worth adding that I've also setup IXTREME to server DHCP and DNS services for the network (isc-dhcp-server & bind9).  So, hosts on the network can only be contacted by name when these two services are up and running.  I'm wondering if maybe nfs-kernel-server is starting up before the DHCP&DNS services during boot ... how could I find out?  Is it possible to specify when nfs-kernel-server starts during the boot process?

Regarding firewall rules:  I use ufw on both server and client.
IXTREME has a ufw rule set to allow all comms in from 192.168.1.0/24.
RASPBMC has a ufw rule set to allow all comms in from IXTREME
both allow all outgoing comms

---

### Post by SeijiSensei on 2015-06-04
Ubuntu Server or a desktop flavor?

On the server version, do you have a file called /etc/rc2.d/S20nfs-kernel-server?  On a desktop, look in /etc/rc5.d.

If that file does not exist, you can fix the problem like this.  Assume we're using rc2.d in this case:
```

cd /etc/rc2.d
sudo ln -s ../init.d/nfs-kernel-server S20nfs-kernel-server
cd /etc/rc6.d
sudo ln -s ../init.d/nfs-kernel-server K80nfs-kernel-server

```
The entry in rc6.d will be the same regardless of whether you used rc2.d or rc5.d.  

The numbers refer to "run levels."  Level 2 is the basic text-only interface; level 5 works on machines with X Windows and a GUI.  Run level 6 is the one used when the system shuts down.  In each case a symbolic link is created to the nfs-kernel-server script that resides in /etc/init.d/.  Links beginning with "S" start a service; those starting with "K" stop it.  The numbers indicate the order in which the scripts are processed.  S20 and K80 are the values assigned on a 14.04 server.

All this is going to be changing once Ubuntu moves fully to systemd.  

I'll just mention that I export /home on the NFS server in my house and never had any problems.

---

### Post by TheFu on 2015-06-05
> **SeijiSensei said:**
> 
I'll just mention that I export /home on the NFS server in my house and never had any problems.

I do too. That is a common design pattern.  It is the NFS mounts below HOME that are on my avoid list. Sorry, I don't recall why it was an issue now.

I've done nested NFS mounts too and that works, provided the order of the mounts is correct. That is for storage outside of HOME.

---

