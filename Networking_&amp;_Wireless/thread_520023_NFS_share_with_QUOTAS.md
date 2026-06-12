---
title: "NFS share with QUOTAS"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by nodows on 2007-08-07
So I'm having a really tough time getting an NFS share to work
with quotas.  

I can access the share just fine with regular parameters like "defaults" or "rw" or "ro",
however I cannot seem to figure out how to add quota support to the share. 

Here's my /etc/exports on the server side
> 
/home/tdavis 192.168.11.102(rw,no_root_squash)

And my fstab on the client side
> 
LABEL=/                 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
sysfs                   /sys                    sysfs   defaults        0 0
LABEL=SWAP-xvda2        swap                    swap    defaults        0 0
# NFS to test quotas on .105
192.168.11.105:/home/tdavis /mnt/home2          nfs     rw              0 0


Now I've read that I can add a line like "userquota" or "groupquota" or
even just "quota" to the 4th field so it woudl say something like
> 
192.168.11.105:/home/tdavis /mnt/home2          nfs     rw,userquota              0 0

But that doesn't seem to work I get an error saying 
> Unsupported nfs mount option: userquota
and it says the same for usrquota,quota,groupquota,etc.  

Now I know I need the rpc.rquotad daemon running,
and I've tried running it on both the server and client side to
no avail.  I've tried adding 'quota' information to the exports
file but it doesn't like it.  And depending on what MAN pages
I read it sounds like what I want to do can and CAN'T be
done at the same time.  Is this a UNIX/BSD only feature?

I've tried forcing manual ports on both sides and no luck,
I've reverted back to the default where it uses portmapper
through port 111 to control all the interaction between the
server/client.  Here's a look at rcpinfo output

> [root@dhcp-desktoplan-102 mnt]# rpcinfo -p localhost
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    639  status
    100024    1   tcp    642  status
    100021    1   udp  32772  nlockmgr
    100021    3   udp  32772  nlockmgr
    100021    4   udp  32772  nlockmgr
    100021    1   tcp  39353  nlockmgr
    100021    3   tcp  39353  nlockmgr
    100021    4   tcp  39353  nlockmgr
    100011    1   udp    894  rquotad
    100011    2   udp    894  rquotad
    100011    1   tcp    897  rquotad
    100011    2   tcp    897  rquotad
[root@dhcp-desktoplan-102 mnt]# rpcinfo -p 192.168.11.105
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    727  status
    100024    1   tcp    730  status
    100011    1   udp   1020  rquotad
    100011    2   udp   1020  rquotad
    100011    1   tcp   1023  rquotad
    100011    2   tcp   1023  rquotad
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32775  nlockmgr
    100021    3   udp  32775  nlockmgr
    100021    4   udp  32775  nlockmgr
    100021    1   tcp  38460  nlockmgr
    100021    3   tcp  38460  nlockmgr
    100021    4   tcp  38460  nlockmgr
    100005    1   udp    609  mountd
    100005    1   tcp    612  mountd
    100005    2   udp    609  mountd
    100005    2   tcp    612  mountd
    100005    3   udp    609  mountd
    100005    3   tcp    612  mountd
[root@dhcp-desktoplan-102 mnt]#    

I'm not sure what else to try... anyone have any ideas?  Anyone
ever try to setup quotas over NFS (successfully) before?

Thanks

---

### Post by nodows on 2007-09-18
bump... a month later... anyone?

---

### Post by klausthorn on 2008-04-04
Hi, according to my first tests I got it working without much fuss, not sure what advice I can give you	:-s

:!: are you sure quota works on the server without nfs? I first tested this by occupying more space and then watching the numbers of [FONT="Courier New"]quota -v[/FONT] and [FONT="Courier New"]repquota -a[/FONT]

Have you checked both kernels for quota support? (I'm NOT sure the client needs it by the way, just brainstorming).

I have no quota-daemon running. During an earlier test this daemon ran wild and had to be stopped. And no group quotas, just user-quotas.
:idea: try: disable the quota-daemons and group quotas

the client did not need any customization, Maybe a reboot or remount. client's /etc/fstab:
[FONT="Courier New"]server:/mnt      /net/mnt  nfs   defaults     0  0[/FONT]

server's /etc/exports:
[FONT="Courier New"]/mnt           *.lan(rw,async,no_root_squash)[/FONT]
:idea: try: async

fstab of the server:
[FONT="Courier New"]/dev/mapper/mnt   /mnt   ext3    defaults,noauto,usrquota 0 0[/FONT]

I use ubuntu 8.04 beta on the server and ubuntu 7.10 on the client (both x86 32bit).
:idea: try: server upgrade 8.04

---

