---
title: "problem with nfs mount in ltsp"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by incin on 2007-03-20
Hi
i have installed the ltsp and followed several how to's and i get the client to boot and he gets the image from the server but when he tries to mount the root filesystem he gets the error:

> Mounting root filesystem: /opt/ltsp/i386 from: 192.168.254.128
mount: 192.168.254.128:/opt/ltsp/i386 failed, reason given by server: Permission denied
mount: nfsmount failed: Bad file descriptor
mount: Mounting 192.168.254.128:/opt/ltsp/i386 on /newroot/nfsroot failed: invalid argument

ERROR! Failed to mount the root directory via NFS!
Possible reasons include:
1 ) NFS services may not be running on the server
2 ) Workstation IP does not map to a hostname, either in /etc/hosts, or in DNS
3 ) Wrong address for NFS server in the DHCP config file
4 ) Wrong pathname for root directory in the DHCP config file

Kernel panic - not syncing: Attempted to kill init!

i have looked in the files that where mentioned in the error but i cant seem to find anything wrong.
the /etc/hosts file have all the addresses that the dhcp gives out and it seems to be right but just in case, here is the first lines in it
> 127.0.0.1 localhost

# the following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.254.128 ip6-localhost ip6-loopback
## LTSP-begin ##
#
# The lines between 'LTSP-begin' and 'LTSP-end' were added
# on: man mar 19 11:56:05 2007, by the ltspcfg configuration tool.
# For more information, visit the LTSP homepage
# at [http://www.LTSP.org](http://www.LTSP.org)
#

192.168.254.1 ws001.ltsp ws001
192.168.254.2 ws002.ltsp ws002
it continues to ip 192.168.254.254 but the dhcp gives out the ip's from 192.168.254.199-192.168.254.254. can anyone see anny errors in the hosts file or do you need to see the dhcp file and so on?

---

### Post by Mr. C. on 2007-03-20
We need to solve 1 problem at a time, starting with the first:

> mount: 192.168.254.128:/opt/ltsp/i386 failed, reason given by server: Permission denied

The server is not allowing the mount.  There can be several reasons for this:

1) source file system directory permissions
2) mount point directory permissions
3) exports

Be sure that allow of these are correct.

Additional information about NFS mounting in general, see week 4 "NFS / Automounter" Notes and Labwork:  

[http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

### Post by incin on 2007-03-21
well the /opt/ltsp/i386 folder have read rights to all
> drwxr-xr-x 20 root root 4096 2007-03-20 09:31 i386
the mount point is the ram of the thinclient i think.. the thinclient i try and boot is a dumb computer that has 128mb ram and a shared prosessor with the server.
I am using vmware server to host the server and the clients, can this make any problems or?
i tried to mount the 192.168.254.128:/opt/ltsp/i386 directly from the server with the root user but i got the same error, i used the command
> root@ltsptest:/# mount 192.168.254.128:/opt/ltsp/i386 /home/test
so it seems even the root user has limits on the folder for some reason :confused:

---

### Post by incin on 2007-03-21
i have now made a completely clean install with a different "how to" the i used the first time.. this time it worked like a charm. but now i need to make the session automatic connect to an rdp session, is there any easy way of doing this?
the "how to" i used was this
[http://help.ubuntu.com/community/ThinClientHowto]("http://help.ubuntu.com/community/ThinClientHowto")
tnx for your help Mr.C

---

### Post by Mr. C. on 2007-03-21
You are likely to get more help on your RDP question if you post it to a new question with the appropriate Title.

MrC

---

