---
title: "NFS issues"
date: 2016-09-19
forum: Networking &amp; Wireless
---

### Post by cscj01 on 2016-09-19
I am running Ubuntu 14.04 x64 and have a home network set up using nfsV3.  Things were fine until my server was having so much trouble that I decided to reinstall 14.04.5 from scratch.  Like a dodo, I didn't backup my /etc/exports file.  Now after the installation, I cannot connect to my server. My /etc/exports file ls:```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#mount.nfs: access denied by server while mounting cp2.local:/media/brenda/Ubuntu_Data_Backup/Data
mount.nfs: access denied by server while mounting cp2.local:/media/brenda/cp2_data/
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
# export of Ubuntu_Data Backup and cp2_data
/media/brenda/Ubuntu_Data_Backup 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)
/media/brenda/cp2_data 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)
#
# Example for NFSv4:mount.nfs: access denied by server while mounting cp2.local:/media/brenda/Ubuntu_Data_Backup/Data
mount.nfs: access denied by server while mounting cp2.local:/media/brenda/cp2_data/
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
```My fstab on my client is```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
# / is on /dec/sdc1
UUID=b61632e9-7186-4ec9-9e4c-214c01d39a4e /     ext4      errors=remount-ro 0       1
# swap is on /dev/sdc3 mount.nfs: access denied by server while mounting cp2.local:/media/brenda/Ubuntu_Data_Backup/Data
mount.nfs: access denied by server while mounting cp2.local:/media/brenda/cp2_data/
UUID=5b3c361f-14a1-45fa-bd52-49cfae3f331b none            swap    sw              0       0
#Entry for /dev/sdd1 :
UUID=00AE2EA54F4183A2	/media/Data	ntfs-3g	 auto,users,uid=1000,gid=1000,umask=000,fmask=137,utfmount.nfs: access denied by server while mounting cp2.local:/media/brenda/Ubuntu_Data_Backup/Data
mount.nfs: access denied by server while mounting cp2.local:/media/brenda/cp2_data/8 0 0
#Entry for /dev/sdb1 :
UUID=3573b59f-77c9-460d-9a29-9f6730954125 /media/Data_One	ext4	errors=remount-ro	0
#Entry for /dev/sda1 :
UUID=9ef58828-ffae-4248-ad25-44596e6440d1 /media/Data_ext4	ext4	errors=remount-ro	0
#Entry for Samba Share drive g on cp2
#//cp2/g	/mnt/cp2	smbfs	iocharset=utf8,uid=1000	0	0

#Entry for NFS Server on drive g on cp2
cp2.local:/media/brenda/Ubuntu_Data_Backup/Data /nfs/Ubuntu_Data_Backup nfs _netdev,vers=3 0 0

#Entry for NFS Server shared documents on cp2s
cp2.local:/media/brenda/cp2_data/ /nfs/cp2_shared_docs nfs _netdev,vers=3 0 0
LABEL=Data_New /media/Data_New auto nosuid,nodev,nofail 0 0
```If I enter```
sudo mount -all
mount.nfs: access denied by server while mounting cp2.local:/media/brenda/Ubuntu_Data_Backup/Data
mount.nfs: access denied by server while mounting cp2.local:/media/brenda/cp2_data/
```If I enter```
showmount -e cp2
clnt_create: RPC: Port mapper failure - Unable to receive: errno 113 (No route to host)

```I am not very proficient with nfs, and I have seen a number of discussion about iptables and opening ports and uid and gid mapping.  I did not have to bother with any of that when I set this up originally.  In fact, I don't recall using ip addresses in my exports file, but I can't remember what I used. So I would appreciate a simple and straight forward approach to get back to what worked.  I suspect it has something to do with nfsv3 on the client and nfsv4 on the server, but that's only a guess on my part based on some of the items I have read.  Any help would be greatly appreciated.

---

### Post by papibe on 2016-09-19
Hi  cscj01.

Comment out the 4th line of your /etc/exports
```
mount.nfs: access denied by server while mounting cp2.local:/media/brenda/cp2_data/
```
restart nfs on the server:
```
sudo service nfs-kernel-server restart
```
If that's doesn't work, could you run these commands in both the server and client, and paste back the results (you can copy/paste the text from the terminal)?
```
ip addr

avahi-resolve-host-name cp2.local

ping cp2.local
```
Regards.

---

### Post by cscj01 on 2016-09-19
The restart was OK.  Fro the client:```
 ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 90:2b:34:df:82:04 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.129/24 brd 192.168.1.255 scope global eth2
       valid_lft forever preferred_lft forever
3: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 90:2b:34:df:82:06 brd ff:ff:ff:ff:ff:ff
``````
avahi-resolve-host-name cp2.local
cp2.local	fe80::216:76ff:febf:86e7

```]```
ping cp2.local
PING cp2.local (192.168.1.128) 56(84) bytes of data.
64 bytes from cp2 (192.168.1.128): icmp_seq=1 ttl=64 time=0.425 ms
64 bytes from cp2 (192.168.1.128): icmp_seq=2 ttl=64 time=0.415 ms
64 bytes from cp2 (192.168.1.128): icmp_seq=3 ttl=64 time=0.450 ms
64 bytes from cp2 (192.168.1.128): icmp_seq=4 ttl=64 time=0.408 ms
64 bytes from cp2 (192.168.1.128): icmp_seq=5 ttl=64 time=0.419 ms
64 bytes from cp2 (192.168.1.128): icmp_seq=6 ttl=64 time=0.430 ms
64 bytes from cp2 (192.168.1.128): icmp_seq=7 ttl=64 time=0.442 ms
64 bytes from cp2 (192.168.1.128): icmp_seq=8 ttl=64 time=0.443 ms
64 bytes from cp2 (192.168.1.128): icmp_seq=9 ttl=64 time=0.444 ms
64 bytes from cp2 (192.168.1.128): icmp_seq=10 ttl=64 time=0.440 ms
```I stopped the ping command.  I also tried this```
rpcinfo -p cp2.local
rpcinfo: can't contact portmapper: RPC: Remote system error - Connection timed out
```I'll get the rest from the server later.  I have to get to a meeting, but will be back in a couple of hours.

---

### Post by papibe on 2016-09-19
Thanks.

Your network sharing segment does not match your actual network.

You are exporting to 192.168.**[COLOR="#FF0000"]0[/COLOR]**.0/255.255.255.0, however your machines are in the 192.168.**[COLOR="#FF0000"]1[/COLOR]**.0/255.255.255.0 subnet.

Change the subnets on your /etc/exports, restart the service on the server, and let us know how it goes.

Hope it helps.
Regards.

P.S.: BTW, you can short your export subnet from 192.168.1.0/255.255.255.0 to 192.168.1.0/24

---

### Post by cscj01 on 2016-09-19
Changed the subnet address and restarted the nfs server.  Then I ran the following with the indicated results:```
showmount -e cp2
clnt_create: RPC: Port mapper failure - Unable to receive: errno 113 (No route to host)
``````
rpcinfo -p cp2.local
rpcinfo: can't contact portmapper: RPC: Remote system error - Connection timed out
```

---

### Post by papibe on 2016-09-20
Are you running a firewall on the server or the client?

Regards.

---

### Post by cscj01 on 2016-09-20
Changed the subnet address and restarted the nfs server.  Then I ran the following with the indicated results:```
showmount -e cp2
clnt_create: RPC: Port mapper failure - Unable to receive: errno 113 (No route to host)
``````
rpcinfo -p cp2.local
rpcinfo: can't contact portmapper: RPC: Remote system error - Connection timed out
```

---

### Post by cscj01 on 2016-09-20
> **papibe said:**
> Are you running a firewall on the server or the client?

Regards.

Yes, I am running ufw on both.

---

### Post by steeldriver on 2016-09-20
IIRC you will need to open at least port 2049 (nfs) and 111 (rpcbind) for incoming connections from your clients

You may also need to fix and open statd/mountd ports as described here [https://wiki.debian.org/SecuringNFS](https://wiki.debian.org/SecuringNFS)

(but it's been a while since I last did it, so things may have changed)

---

### Post by cscj01 on 2016-09-20
> **steeldriver said:**
> IIRC you will need to open at least port 2049 (nfs) and 111 (rpcbind) for incoming connections from your clients

You may also need to fix and open statd/mountd ports as described here [https://wiki.debian.org/SecuringNFS](https://wiki.debian.org/SecuringNFS)

(but it's been a while since I last did it, so things may have changed)

Those ports are open on the client(s).  I did not have to do any of the items mentioned in the link you referenced when I initially set the network up.  I installed the nfs software on server and client, created my /etc/exports file, and things worked.  Of course I used nfsv3 which I still use.  Have things gotten so complicated since when I first installed?  The link doesn't say which (server or client) to edit with these files.  I know the /etc/default/nfs-kernel-server is on the server, but I don't have a /etc/default/quota file on either, and I have a /etc/default/nfs-common on both client and server.  I do not have a /etc/modprobe.d/local.conf on either as well.  My /etc/services file includes both ports 111 (portmapper) and 2049 (nfs) on both client and server.  So it seems that the requirements for setting up a simple home network with nfsv3 has become increasing complex.  At this point, I'm not sure what to do next.  If only I had saved my /etc/exports file from before!

BTW, I appreciate your suggestions.  I just don't know how to proceed.

---

### Post by JKyleOKC on 2016-09-20
I'm having a somewhat similar problem here, which may be related to a relatively recent system upgrade; mine isn't identical to yours, but the "no route to host" error message you reported a bit earlier sounds as if they may be related. Run either of these commands (they do the same report but present it differently): "route -n" or "ip route" and post your results. In my case, I'm failing to get my routes set properly when I reboot, and have to set them manually. It's possible that your subnet error may have caused the lack of a route but the report Isuggest here will show us for sure.

You'll need to open ports 2049 and 111 on both the client and the server; I don't use UFW so will have to leave the details of doing so to steeldriver. If possible with UIFW you should restrict the port openings to the specific IP addresses of your two machines, so that nobody else can access portmapper -- it can easily become a security problem!

---

### Post by steeldriver on 2016-09-20
AFAIK the client doesn't need any specific ports open (the default "allow outgoing/established - deny incoming" rule should do)

On the server, try

```

sudo ufw allow from 192.168.1.0/24 to any port 2049

sudo ufw allow from 192.168.1.0/24 to any port 111

```

Let's not start modifying /etc/defaults files until you've tried that

---

### Post by cscj01 on 2016-09-20
> **JKyleOKC said:**
> I'm having a somewhat similar problem here, which may be related to a relatively recent system upgrade; mine isn't identical to yours, but the "no route to host" error message you reported a bit earlier sounds as if they may be related. Run either of these commands (they do the same report but present it differently): "route -n" or "ip route" and post your results. In my case, I'm failing to get my routes set properly when I reboot, and have to set them manually. It's possible that your subnet error may have caused the lack of a route but the report Isuggest here will show us for sure.

You'll need to open ports 2049 and 111 on both the client and the server; I don't use UFW so will have to leave the details of doing so to steeldriver. If possible with UIFW you should restrict the port openings to the specific IP addresses of your two machines, so that nobody else can access portmapper -- it can easily become a security problem!

Here are the two commands executed from the client:```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth2
``````
ip route
default via 192.168.1.1 dev eth2  proto static 
192.168.1.0/24 dev eth2  proto kernel  scope link  src 192.168.1.129  metric 1
```

---

### Post by cscj01 on 2016-09-20
> **steeldriver said:**
> AFAIK the client doesn't need any specific ports open (the default "allow outgoing/established - deny incoming" rule should do)

On the server, try

```

sudo ufw allow from 192.168.1.0/24 to any port 2049

sudo ufw allow from 192.168.1.0/24 to any port 111

```

Let's not start modifying /etc/defaults files until you've tried that

After adding the two rules to ufw, I get the following:```
rpcinfo -p cp2.local
   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  51718  status
    100024    1   tcp  44551  status
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100021    1   udp  34529  nlockmgr
    100021    3   udp  34529  nlockmgr
    100021    4   udp  34529  nlockmgr
    100021    1   tcp  34549  nlockmgr
    100021    3   tcp  34549  nlockmgr
    100021    4   tcp  34549  nlockmgr
    100005    1   udp  44924  mountd
    100005    1   tcp  53652  mountd
    100005    2   udp  33170  mountd
    100005    2   tcp  53545  mountd
    100005    3   udp  37477  mountd
    100005    3   tcp  58171  mountd
``````
showmount -e cp2
clnt_create: RPC: Port mapper failure - Unable to receive: errno 113 (No route to host)
``````
showmount -e cp2.local
rpc mount export: RPC: Timed out
```

---

### Post by steeldriver on 2016-09-20
Well FWIW on my HTPC box I **have** done the fixed rpc.mountd mod in my /etc/defaults/nfs-kernel-server:

```

$ grep -B5 '32767' /etc/default/nfs-kernel-server
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information,
# see rpc.mountd(8) or http://wiki.debian.org/SecuringNFS
# To disable NFSv4 on the server, specify '--no-nfs-version 4' here
#RPCMOUNTDOPTS=--manage-gids
**RPCMOUNTDOPTS="--manage-gids -p 32767"**

```

and then added ufw rule

```

sudo ufw allow from 192.168.1.0/24 to any port 32767

```

I also get the timeout if I delete the rule:

```

$ showmount -e htpc-01.local
rpc mount export: RPC: Timed out

```

So it looks like it is necessary (at least in this configuration).

---

### Post by JKyleOKC on 2016-09-20
Your route table reports look okay -- not at all like the ones I get when my problem is being active. Looks as if steeldriver is following the proper path for you!

---

### Post by cscj01 on 2016-09-20
> **steeldriver said:**
> Well FWIW on my HTPC box I **have** done the fixed rpc.mountd mod in my /etc/defaults/nfs-kernel-server:

```

$ grep -B5 '32767' /etc/default/nfs-kernel-server
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information,
# see rpc.mountd(8) or http://wiki.debian.org/SecuringNFS
# To disable NFSv4 on the server, specify '--no-nfs-version 4' here
#RPCMOUNTDOPTS=--manage-gids
**RPCMOUNTDOPTS="--manage-gids -p 32767"**

```

and then added ufw rule

```

sudo ufw allow from 192.168.1.0/24 to any port 32767

```

I also get the timeout if I delete the rule:

```

$ showmount -e htpc-01.local
rpc mount export: RPC: Timed out

```

So it looks like it is necessary (at least in this configuration).

Ok, where do I make this modification?  I have specified --no-nfs-version 4 in nfs-kernel-server.  Are you saying I should specify a fixed port in that file?  Is there any thing special about port number 32767?  I understand adding the rule to ufw.

---

### Post by steeldriver on 2016-09-20
The modification is made in the /etc/default/nfs-kernel-server file

I just used the port number suggested in the Debian docs

You will need to restart nfs-kernel-server for it to take effect

---

### Post by cscj01 on 2016-09-20
That seems to have done it.  Thanks to all who offered suggestions and advice.  Now I have to find out why luckybackup cannot see the mounted nfs shares.  I can see them.  Oh well, if there were no problems, I'd probably be bored.  Thank you again to everyone.

---

### Post by cscj01 on 2016-09-21
That seems to have done it.  Thanks to all who offered suggestions and advice.  Now I have to find out why luckybackup cannot see the mounted nfs shares.  I can see them.  Oh well, if there were no problems, I'd probably be bored.  Thank you again to everyone.

---

