---
title: "Unable to mount Unraid NAS share"
date: 2024-09-27
forum: Networking &amp; Wireless
---

### Post by makem2 on 2024-09-27
I am using Ubuntu 24.04 and have nfs-utils installed.

I have built a NAS and am trying to access a share on it.

```

makem@makem-22:~$ sudo mount -t nfs4 192.168.1.249/data /media/nas-media
[sudo] password for makem: 
mount: /media/nas-media: bad option; for several filesystems (e.g. nfs, cifs) you might need a /sbin/mount.<type> helper program.
       dmesg(1) may have more information after failed mount system call.
makem@makem-22:~$

```

I am not sure what to look for in dmesg.

Edit: Installed nfs-common:

```

sudo mount -t nfs4 192.168.1.249/data /media/nas-media
mount.nfs4: remote share not in 'host:dir' format

```

The share is exported in the NAS but under the SMB SECURITY SETTINGS

Does that mean only SMB sharing?

---

### Post by TheFu on 2024-09-27
I know nothing at all about Unraid.  I do know NFS.

nfs4 is wrong. Use nfs instead.    The client and server will negotiate the version supported.   The command it missing a ':' as well.

To be clear, 
```
sudo      mount        -t [COLOR="#FF0000"]nfs[/COLOR]      192.168.1.249[COLOR="#FF0000"]:[/COLOR]/data     /media/nas-media
```

This assumes that 
```
showmount -e 192.168.1.249
```
shows 192.168.1.249:/data as being exported 
AND
it assumes that  /media/nas-media directory exists already.

I am a bit worried that the IP is being provided via DHCP.  Servers need static IPs, which are typically under .20 in a home environment. Using DHCP with a server is asking for problems. It will happen eventually.

---

### Post by makem2 on 2024-09-27
> **TheFu said:**
> I know nothing at all about Unraid.  I do know NFS.

nfs4 is wrong. Use nfs instead.    The client and server will negotiate the version supported.   The command it missing a ':' as well.

To be clear, 
```
sudo      mount        -t [COLOR=#FF0000]nfs[/COLOR]      192.168.1.249[COLOR=#FF0000]:[/COLOR]/data     /media/nas-media
```

This assumes that 
```
showmount -e 192.168.1.249
```
shows 192.168.1.249:/data as being exported 
AND
it assumes that  /media/nas-media directory exists already.

I am a bit worried that the IP is being provided via DHCP.  Servers need static IPs, which are typically under .20 in a home environment. Using DHCP with a server is asking for problems. It will happen eventually.

```

makem@makem-22:~$ sudo mount -t nfs 192.168.1.249:/data /media/nas-media
[sudo] password for makem: 
Created symlink /run/systemd/system/remote-fs.target.wants/rpc-statd.service &#8594; /usr/lib/systemd/system/rpc-statd.service.


```

Above did not finish.

```
makem@makem-22:~$showmount -e 192.168.1.249clnt_create: RPC: Unable to receive
makem@makem-22:~$


```

The IP address is static, being set in the router. Typo ':' as I was aware that should be there.

I will have to find how Unraid exports - surely not just Windows when its Linux based.

Thank you for your time (I was aware of your NFS knowledge and preference)

Edit: /media/nas-media directory exists.

---

### Post by TheFu on 2024-09-27
Ah ... the dreaded RPC boot-timing issue.  So, NFS is dependent on a few other services that need to work BEFORE it can work.  I don't have them memorized, sorry.  In general, the easiest solution is to reboot the server (your NAS) and reboot the NFS client.  That fixes this issue 90% of the time.  If it doesn't you'll need to dig into each depend service looking at log files (or journalctl) to figure out which isn't starting  up, determine the issue and fix that.  A few months ago, one of my NFS servers had the rpc.service refuse to start - no NFS workie.  I don't recall the exact issue now, but something like /var/ had gotten full is typical.  There's no way anyone here would know to ask those things, so you'll need to figure out why a service that nfs depends on isn't starting.

[https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/4/html/reference_guide/ch-nfs](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/4/html/reference_guide/ch-nfs) says this, which I didn't know:
> NFSv4 has no interaction with portmapper, rpc.mountd, rpc.lockd, and rpc.statd, since they have been rolled into the kernel. NFSv4 listens on the well known TCP port 2049. 
NFS is the same on all Linux systems, so don't worry that the link is for RH.  On my 20.04 NFS servers, rpcbind.service is still required to work.  The rpc-statd.service is not, though is is running to support NFSv3 clients.

Also, there are a few firewall ports that need to be open on the NFS server.  I force 111, 2049 and 13025 ports to be allowed in from my NFS client systems to the server.  13025 is non-standard. I configured that port separately for some reason I don't recall now.

Is your "NAS" a commercial product that would not be a generic Linux distro?

---

### Post by makem2 on 2024-09-27
> **TheFu said:**
> Ah ... the dreaded RPC boot-timing issue.  So, NFS is dependent on a few other services that need to work BEFORE it can work.  I don't have them memorized, sorry.  In general, the easiest solution is to reboot the server (your NAS) and reboot the NFS client.  That fixes this issue 90% of the time.  If it doesn't you'll need to dig into each depend service looking at log files (or journalctl) to figure out which isn't starting  up, determine the issue and fix that.  A few months ago, one of my NFS servers had the rpc.service refuse to start - no NFS workie.  I don't recall the exact issue now, but something like /var/ had gotten full is typical.  There's no way anyone here would know to ask those things, so you'll need to figure out why a service that nfs depends on isn't starting.

[https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/4/html/reference_guide/ch-nfs](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/4/html/reference_guide/ch-nfs) says this, which I didn't know:

NFS is the same on all Linux systems, so don't worry that the link is for RH.  On my 20.04 NFS servers, rpcbind.service is still required to work.  The rpc-statd.service is not, though is is running to support NFSv3 clients.

Edit: [https://unraid.net/](https://unraid.net/)

Also, there are a few firewall ports that need to be open on the NFS server.  I force 111, 2049 and 13025 ports to be allowed in from my NFS client systems to the server.  13025 is non-standard. I configured that port separately for some reason I don't recall now.

Is your "NAS" a commercial product that would not be a generic Linux distro?

Wow, that is a lot to digest. No, I personally built it from scratch and the OS is on an SD card which must be present as it is loaded into ram on every boot.

I will reboot with crossed fingers and report back.

---

### Post by makem2 on 2024-09-27
I am getting this error now:

```

makem@makem-22:~$ sudo mount -t nfs 192.168.1.249:/data /media/nas-media
[sudo] password for makem: 
mount.nfs: access denied by server while mounting 192.168.1.249:/data
makem@makem-22:~$ 

```

My son set up Unraid and I remember although I usually use makem as username he asked me to use makem1. I have a makem1 account accessible by makem.

I think I will leave well alone as I am so close until he returns next week.

Edit: May be of interest as 2 errors mentioned:

```

makem@makem-22:~$ sudo mount -t nfs 192.168.1.249:/data /media/nas-media
[sudo] password for makem: 
mount.nfs: access denied by server while mounting 192.168.1.249:/data
makem@makem-22:~$ sudo mount -t nfs -vvv 192.168.1.249:/data /media/nas-media
mount.nfs: timeout set for Fri Sep 27 17:01:01 2024
mount.nfs: trying text-based options 'vers=4.2,addr=192.168.1.249,clientaddr=192.168.1.59'
mount.nfs: mount(2): No such file or directory
mount.nfs: trying text-based options 'addr=192.168.1.249'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.1.249 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 192.168.1.249 prog 100005 vers 3 prot UDP port 50462
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting 192.168.1.249:/data
makem@makem-22:~$

```

On the NAS:

```

root@nas:~# showmount -e
Export list for nas:
/mnt/user/data *
root@nas:~# 

```

My previous showmount was on the client without the nas IP :-(

On the NAS:

/etc/exports shows:

"/mnt/user/data" -fsid=100,async,no_subtree_check *(rw,sec=sys,insecure,anongid=100,anonuid=99,all_squash)

---

### Post by makem2 on 2024-09-27
@TheFu, Reading [https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/4/html/reference_guide/ch-nfs#s1-nfs-how](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/4/html/reference_guide/ch-nfs#s1-nfs-how)

[SIZE=2]I find that the NAS does not have an[SIZE=2] [SIZE=3][COLOR=#000000][FONT=RedHatMono]/etc/exports directory [/FONT][/COLOR][/SIZE][/SIZE][/SIZE][COLOR=#151515][FONT=RedHatText][SIZE=3]to determine whether the client is allowed to access any of the exported file systems. As mentioned in the above url.[/SIZE]


[/FONT][/COLOR]

---

### Post by TheFu on 2024-09-27
> **makem2 said:**
> 
```

makem@makem-22:~$ sudo mount -t nfs 192.168.1.249:/data /media/nas-media
[sudo] password for makem: 
mount.nfs: access denied by server while mounting 192.168.1.249:/data
makem@makem-22:~$ sudo mount -t nfs -vvv 192.168.1.249:/data /media/nas-media
mount.nfs: timeout set for Fri Sep 27 17:01:01 2024
mount.nfs: trying text-based options 'vers=4.2,addr=192.168.1.249,clientaddr=192.168.1.59'
mount.nfs: mount(2): No such file or directory
mount.nfs: trying text-based options 'addr=192.168.1.249'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.1.249 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 192.168.1.249 prog 100005 vers 3 prot UDP port 50462
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting 192.168.1.249:/data
makem@makem-22:~$

```

On the NAS:

```

root@nas:~# showmount -e
Export list for nas:
/mnt/user/data *
root@nas:~# 

```

My previous showmount was on the client without the nas IP :-(

On the NAS:

/etc/exports shows:

```
/mnt/user/data -fsid=100,async,no_subtree_check *(rw,sec=sys,insecure,anongid=100,anonuid=99,all_squash)
```

Has some options I've never seen before. I suspect they aren't necessary.  An export on one of my NFS servers, converted for your situation (but with the wrong subnet) has this:
```
/mnt/user/data    [COLOR="#FF0000"]172.22.22.0/24[/COLOR](fsid=4,rw,async,no_subtree_check)
```

The main difference is that I restrict the allowed client subnet to one of my subnets.    I think you have 3 fields when there should only be 2 fields.  A field is separated by one or more whitespace characters.  I'm amazed it ever worked before, if it did.

For another NFS server, I have 1 export line for each client to each exported file system. That exports file has 63 lines (a bit cumbersome, I agree).
```
/d/D1           deneb(rw,async,root_squash,no_subtree_check,fsid=1)
/d/D1           posc(rw,async,root_squash,no_subtree_check,fsid=1)
```
Because I run a LAN DNS server, the hostnames map to specific IPs, but that is hidden.  Most people would just have 1 line and use something like 192.168.24.0/24 as their network limiting option.

---

### Post by makem2 on 2024-09-27
> **TheFu said:**
> Has some options I've never seen before. I suspect they aren't necessary.  An export on one of my NFS servers, converted for your situation (but with the wrong subnet) has this:
```
/mnt/user/data    [COLOR=#FF0000]172.22.22.0/24[/COLOR](fsid=4,rw,async,no_subtree_check)
```

The main difference is that I restrict the allowed client subnet to one of my subnets.    I think you have 3 fields when there should only be 2 fields.  A field is separated by one or more whitespace characters.  I'm amazed it ever worked before, if it did.

For another NFS server, I have 1 export line for each client to each exported file system. That exports file has 63 lines (a bit cumbersome, I agree).
```
/d/D1           deneb(rw,async,root_squash,no_subtree_check,fsid=1)
/d/D1           posc(rw,async,root_squash,no_subtree_check,fsid=1)
```
Because I run a LAN DNS server, the hostnames map to specific IPs, but that is hidden.  Most people would just have 1 line and use something like 192.168.24.0/24 as their network limiting option.

'I think you have 3 fields when there should only be 2 fields. A field is separated by one or more whitespace characters.'

I don't understand that but I think lets leave it until my son returns. I find he has put a 'data' directory in as a user! So it looks like I may have to set it up again from scratch with the proper paths layout. He is a Windows user.

---

### Post by TheFu on 2024-09-27
MS-Windows users aren't gonna help you with Unix problems.  Whatever. Good luck.  The way that an MS-Windows user looks at storage is very, very, different from how Unix sees it.

---

### Post by makem2 on 2024-09-28
> **TheFu said:**
> MS-Windows users aren't gonna help you with Unix problems.  Whatever. Good luck.  The way that an MS-Windows user looks at storage is very, very, different from how Unix sees it.

Yes, he knows very little about Unix, but, I want him to know why I have a problem and how I need to sort it.

Btw, I can easily make an SMB share :-(

---

### Post by TheFu on 2024-09-28
3 fields where there should only be 2.

```
/mnt/user/data       -fsid=100,async,no_subtree_check     *(rw,sec=sys,insecure,anongid=100,anonuid=99,all_squash)
```

So, I've re-read the manpage for the /etc/exports file and **I'm 100% wrong.**  They show an example that appears to be like what that file you posted has.  Their example setting:
```
/srv/www        -sync,rw server @trusted @external(ro)
```
The manpage explanation for the line is this:
> exports a directory read-write to the machine 'server' as well  as  the  `@trusted'  netgroup,  and  read-only to netgroup `@external', all three mounts with the `sync' option enabled. 
Netgroups are from NIS and NIS+. I suspect netgroups can be setup in LDAP too. They are not in a locally managed file, except on the LDAP or NIS+ server.  Since 2000, nobody should be using NIS, anywhere, due to security issues.  From a functionality standpoint, NIS was awesome. It was a trivial way to centralize hosts, users, groups for entire networks with SSO capabilities. Since NIS, all other SSO/centralized user management has been a pain to use.

I'm going to test this multi-field method of exporting now.  It would greatly simplify my /etc/exports, if it works.  Ok, the test show this method works. Excellent. If you weren't resistant, I wouldn't have learned this, so THANK YOU!
My test was this line:
```
/d/rom/export/www/gallery     -fsid=4,rw,async,no_subtree_check     deneb istar nextcloud-lxd posc rpi r-pi3 pi4
```
That's 3 fields ...  er ... sorta.  
[LIST=1]
[*]The exported directory, 
[*]all the options, and 
[*]each system to be granted access. These are actually separate fields by the definition, but since they are at the end of the line, I group them in to 1 field arbitrarily.  That's not really true.  Those hostnames (really DNS lookups) could be a list of IP address or a subnet or a wildcard like *.thefu.lan or *.local (if you run avahi/mDNS).
[/LIST]
This prevents access by anyone who happens to plug into an ethernet port without any thought.  I want those client systems to have access to all our family and vacation photos, when they are on our trusted network.  But whenever a house guest plugs into the ethernet port in their bedroom (I don't do wifi), they don't get access.

Just occurred to me, 
```
/mnt/user/data   -fsid=100,async,no_subtree_check,rw,sec=sys,insecure,anongid=100,anonuid=99,all_squash * 
```
is the same for that export.  That '*' at the end should scare you a bit.

Thanks again.  I need to go and simplify all the other export lines now.

---

### Post by makem2 on 2024-09-30
> **TheFu said:**
> 3 fields where there should only be 2.

```
/mnt/user/data       -fsid=100,async,no_subtree_check     *(rw,sec=sys,insecure,anongid=100,anonuid=99,all_squash)
```

So, I've re-read the manpage for the /etc/exports file and **I'm 100% wrong.**  They show an example that appears to be like what that file you posted has.  Their example setting:
```
/srv/www        -sync,rw server @trusted @external(ro)
```
The manpage explanation for the line is this:

Netgroups are from NIS and NIS+. I suspect netgroups can be setup in LDAP too. They are not in a locally managed file, except on the LDAP or NIS+ server.  Since 2000, nobody should be using NIS, anywhere, due to security issues.  From a functionality standpoint, NIS was awesome. It was a trivial way to centralize hosts, users, groups for entire networks with SSO capabilities. Since NIS, all other SSO/centralized user management has been a pain to use.

I'm going to test this multi-field method of exporting now.  It would greatly simplify my /etc/exports, if it works.  Ok, the test show this method works. Excellent. If you weren't resistant, I wouldn't have learned this, so THANK YOU!
My test was this line:
```
/d/rom/export/www/gallery     -fsid=4,rw,async,no_subtree_check     deneb istar nextcloud-lxd posc rpi r-pi3 pi4
```
That's 3 fields ...  er ... sorta.  
[LIST=1]
[*]The exported directory,
[*]all the options, and
[*]each system to be granted access. These are actually separate fields by the definition, but since they are at the end of the line, I group them in to 1 field arbitrarily.  That's not really true.  Those hostnames (really DNS lookups) could be a list of IP address or a subnet or a wildcard like *.thefu.lan or *.local (if you run avahi/mDNS).
[/LIST]
This prevents access by anyone who happens to plug into an ethernet port without any thought.  I want those client systems to have access to all our family and vacation photos, when they are on our trusted network.  But whenever a house guest plugs into the ethernet port in their bedroom (I don't do wifi), they don't get access.

Just occurred to me, 
```
/mnt/user/data   -fsid=100,async,no_subtree_check,rw,sec=sys,insecure,anongid=100,anonuid=99,all_squash * 
```
is the same for that export.  That '*' at the end should scare you a bit.

Thanks again.  I need to go and simplify all the other export lines now.

You are welcome @TheFu. You have assisted me several times over the years so it is about time I paid back something ;-)

---

### Post by makem2 on 2024-09-30
[COLOR=#0C0D0E][FONT=-apple-system][COLOR=var(--black-300) !important][FONT=inherit][COLOR=var(--theme-body-font-color, var(--black-600)) !important][FONT=inherit][COLOR=var(--theme-body-font-color, var(--black-600))][FONT=inherit]
[/FONT][/COLOR][/FONT][/COLOR]
[/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system][FONT=var(--theme-post-body-font-family]Server permissions (Includes data/ subject of mount):
```

root@nas:/mnt/user# ls -lh
total 0
lrwxrwxrwx 1 nobody users 152 Sep 25 18:08 appdata -> ../cache/appdata/
drwxrwxrwx 1 nobody users  84 Sep 28 18:00 appdata_backup/
drwxrwxrwx 1 nobody users  16 Sep 27 19:30 data/
drwxrwxrwx 1 nobody users   0 Aug 11 22:26 domains/
drwxrwxrwx 1 nobody users   6 Sep 30 13:43 han-domain/
drwxrwxrwx 1 nobody users   6 Aug 11 22:26 isos/
drwxrwxrwx 1 nobody users  22 Sep 27 20:01 my-domain/
drwxrwxrwx 1 nobody users  26 Aug 11 22:26 system/
root@nas:/mnt/user#[/FONT]
[/FONT][/COLOR]

```

[COLOR=#0C0D0E][FONT=-apple-system]Ubuntu 24.04 mount point named nas-media:[/FONT][/COLOR]
```

makem@makem-22:/media$ ls -lh
total 12K
drwxrwxrwx 1 root  root  4.0K Sep 27 00:58 games
drwxr-xr-x 7 root  root  4.0K Sep 30 13:17 makem
drwxr-xr-x 2 makem makem 4.0K Sep 27 12:53 nas-media

```

[FONT=-apple-system]Linux mount command:

```
[/FONT]

makem@makem-22:/media$ sudo mount  -t nfs 192.168.1.249:/data /media/nas-media
mount.nfs: access denied by server while mounting 192.168.1.249:/data
makem@makem-22:/media$

```

I fail to see why it is denied.

---

### Post by makem2 on 2024-09-30
correct command (Path)

sudo mount  -t nfs 192.168.1.249:/mnt/user/data /media/nas-media

---

