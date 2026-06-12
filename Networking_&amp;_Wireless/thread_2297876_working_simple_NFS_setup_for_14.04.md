---
title: "working simple NFS setup for 14.04"
date: 2015-10-07
forum: Networking &amp; Wireless
---

### Post by geoff07 on 2015-10-07
I struggled for ages getting nfs working between a number of laptops and my main desktop on my home network. My lack of ability was compounded by the many complicated and in some cases outdated advice pages on the web.  Many steps are suggested, some of which seem redundant (portmap changes, changing users to 'nobody', etc.). I spent quite some time working through my problem from first principles, and offer a solution here. I hope it is useful to you. I don't guarantee that this is the simplest solution, only that it works for me.  Any improvements are welcome if they retain the simplicity.  The features are:

- Ubuntu 14.04 on all machines
- Specific directories are being shared, yours are likely to be different
- the linked folders show up in the laptop-user's home directory
- no security beyond the basic level, assuming no hostile interlopers on the local network segment and a good router firewall to the world. If that is not your situation then you need a better solution than this.
- identical userids and user numbers on all machines, in this case only one: 'stuart'

```

_On the host server (IP 192.168.1.66 in this example)_
Host directories to access on the clients:
    /home/Downloads
    /home/Documents
    /home/eagle
    /media/stuart/svr_data

Ensure NFS and NTP software is installed. NFS requires accurate time on server and client to ensure proper timestamping
    sudo apt-get update
    sudo apt-get install nfs-kernel-server ntp

Make the export filesystem by creating the empty directories
    sudo mkdir /export/Downloads
    sudo mkdir /export/Documents
    sudo mkdir /export/eagle
    sudo mkdir /export/svr_data

Create list of shares in file: /etc/exports. The name on the left will appear under the mount point specified in the client fstab.  All clients on the subnet x.x.x.0 – x.x.x.255 have access
    /home/stuart/Downloads	192.168.1.0/24(rw,sync,no_root_squash,no_subtree_check) 
    /home/stuart/Documents	192.168.1.0/24(rw,sync,no_root_squash,no_subtree_check)
    /home/stuart/eagle		192.168.1.0/24(rw,sync,no_root_squash,no_subtree_check)
    /media/stuart/svr_data      192.168.1.0/24(rw,sync,no_subtree_check) 

Make shares by exporting names so clients can see them every time /etc/exports changes
    sudo exportfs -a

Put binding command in the host fstab so every reboot sets up nfs
    /home/stuart/Downloads		/export/Downloads	none	bind	0	0  
    /home/stuart/Documents		/export/Documents	none	bind	0	0 
    /home/stuart/eagle			/export/eagle		none	bind	0	0 
    /media/stuart/svr_data		/export/svr_data	none	bind	0	0

Start NFS with
    sudo service nfs-kernel-server [re]start 

_On the client (any in range IP 192.168.1.xxx)_

Ensure NFS and NTP software is installed
    sudo apt-get update
    sudo apt-get install nfs-common ntp

Create somewhere to mount shares. All will go under this directory
    sudo mkdir /mnt/nfs

Mount the entire exported tree by adding line to the client fstab so every reboot sets up nfs
    192.168.1.66:/		/mnt/nfs 	nfs	auto	0	0

See what is mounted
    less /proc/mounts 	        [lists all]
    mount -t nfs 		[lists just nfs mounts]
    df -h		        [shows accessible space]

Now make the shared folders accessible within the normal user home directory
    sudo ln -sv /mnt/nfs/home/stuart/Documents 	/home/stuart/svr_Documents
    sudo ln -sv /mnt/nfs/home/stuart/Downloads 	/home/stuart/svr_Downloads
    sudo ln -sv /mnt/nfs/home/stuart/eagle 	/home/stuart/svr_eagle
    sudo ln -sv /mnt/nfs/media/stuart/svr_data 	/home/stuart/svr_data

```

---

### Post by geoff07 on 2015-10-12
I'm now finding that if the server suspends and then restarts there is a problem with maintaining the mounts, and the client fstab needs to be re-invoked (reboot or mount -a). At least, that is my take on it. Any other ideas regarding how to ensure the client will always be able to access the host even if the host has suspended and restarted in the meantime?

---

