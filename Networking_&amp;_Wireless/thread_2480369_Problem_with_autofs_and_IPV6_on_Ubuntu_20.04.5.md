---
title: "Problem with autofs and IPV6 on Ubuntu 20.04.5"
date: 2022-10-27
forum: Networking &amp; Wireless
---

### Post by georgesgiralt on 2022-10-27
Hello,
I used sucessfully autofs to access my home directory on my local network using ipv4. For example on one computer my /etc/exports is like this :
```
/home/georges 192.168.0.0/24(rw,sync,no_subtree_check)
```
and on another computer I have in my auto.computer1 file : 
```
georges -fstype=nfs -rw,hard,intr computer1.local:/home/georges
```
This worked fine for a long time. But my ISP has switched everything to use IPV6 and now when I ping a local hostname I get : 
```
 ping computer1.local
PING computer1.local(computer1.local (2a01:e0a:26a:7d20:9cb0:2bba:7dc4:cf4c%3)) 56 data bytes
64*octets de computer1.local (2a01:e0a:26a:7d20:9cb0:2bba:7dc4:cf4c)*: icmp_seq=1 ttl=64 temps=4.72*ms
```
So I changed the export file to :
```
/home/georges 192.168.0.0/24(rw,sync,no_subtree_check)
/home/georges 2a01:e0a:26a:7d20::/64(rw,sync,no_subtree_check)
```
And when I try to get an nfs mount i get : 
```

# mount.nfs computer1.local:/home/georges /mnt
mount.nfs: an incorrect mount option was specified
```
and on syslog I get : 
```

Oct 27 17:47:04 computer2 kernel: [ 6889.087318] NFS: bad IP address specified: addr=2a01:e0a:26a:7d20:9cbf:5a2a:112:c1d5%3
Oct 27 17:47:04 computer2 kernel: [ 6889.087451] NFS: bad IP address specified: addr=2a01:e0a:26a:7d20:9cbf:5a2a:112:c1d5%3
Oct 27 17:47:04 computer2 kernel: [ 6889.087575] NFS: bad IP address specified: addr=2a01:e0a:26a:7d20:9cbf:5a2a:112:c1d5%3
Oct 27 17:47:04 computer2 kernel: [ 6889.394666] NFS: bad IP address specified: addr=2a01:e0a:26a:7d20:9cbf:5a2a:112:c1d5%3

```

I cant figure out from where the %3 on the IPV6 addr comes from and what incorrect mount option could be.
So all help I can get will be appreciated.

---

### Post by TheFu on 2022-10-27
```
georges [s]-fstype=nfs -rw,hard,intr[/s] computer1.local:/home/georges
```
should be
```
georges -fstype=nfs,rw,hard,intr      computer1.local:/home/georges
```

There are 3 fields in the autofs mount lines, not 4.
This assumes you can 
$ ping computer1.local

If avahi or DNS aren't working, this will fail.

I've also made an assumption about the contents of the auto.master file that references this file, but whatever.

---

### Post by georgesgiralt on 2022-10-28
Hello TheFu ,
Thank you for your answer. 
My auto.master, and auto.computer1 where not modified in ages, so their format may not be optimal for the current Ubuntu version I use today. But I'll try your suggested format in order to ascertain this is not the cause of my trouble.
As per the auto.master file, it contains lines like this one, one for each computer i intend to use :
```

/computer1	/etc/auto.computer1  --timeout=30 --ghost
```
And, yes, I can ping all my computers in the local network and this gives IPV6 name resolution and response. 
```

ping -c 1 computer1.local
PING computer1.local(computer1.local (xxxx:xxx:xxx:xxx:xxxx:xxx:f1e4:2f6d%3)) 56 data bytes
64*octets de computer1.local (xxxx:xxx:xxx:xxx:xxxx:xxx:f1e4:2f6d)*: icmp_seq=1 ttl=64 temps=10.2*ms

```
As you can see, in the above IPV6 addresses, there are also the %3 characters... 
I'm wondering if autofs (and nfs stack) are IPV6 capable on ubuntu ?

---

### Post by georgesgiralt on 2022-10-28
No joy. 
Even with the suggested modification of the auto.computer1 file syntax, the behaviour is the same. 
```
georges -fstype=nfs,rw,hard,intr computer1.local:/home/georges
```
gave : 
```
$cd /computer1/georges
-bash: cd: /computer1/georges: No such file or directory
```
and the syslog has : 
```

Oct 28 07:07:50 computer1 systemd[1]: Started NFS status monitor for NFSv2/3 locking..
Oct 28 07:07:50 computer1 kernel: [ 2663.724448] NFS: bad IP address specified: addr=xxxx:xxx:xxx:xxxx:xxxx:xxxx:f1e4:2f6d%3
Oct 28 07:07:50 computer1 kernel: [ 2663.762382] NFS: bad IP address specified: addr=xxxx:xxx:xxx:xxxx:xxxx:xxxx:f1e4:2f6d%3
Oct 28 07:07:50 computer1 kernel: [ 2663.762497] NFS: bad IP address specified: addr=xxxx:xxx:xxx:xxxx:xxxx:xxxx:f1e4:2f6d%3
Oct 28 07:07:50 computer1 kernel: [ 2663.762603] NFS: bad IP address specified: addr=xxxx:xxx:xxx:xxxx:xxxx:xxxx:f1e4:2f6d%3
Oct 29 07:07:50 computer1 kernel: [ 2663.808055] NFS: bad IP address specified: addr=xxxx:xxx:xxx:xxxx:xxxx:xxxx:f1e4:2f6d%3
```

---

### Post by TheFu on 2022-10-28
I assume after any changes to the auto* files, you are restarting the autofs service, right?  If not, the changes don't get seen.

The quick answer to determine if this is NFS or name resolution is to use a manual mount, using the IPv6 address, and see if that works.
```
sudo mount      -t nfs       -o rw,hard,intr       xxxx:xxx:xxx:xxx:xxxx:xxx:f1e4:2f6d:/home/georges        /computer1/georges
```
The /computer1/georges directory needs to already exist, BTW.  If it doesn't, that mount will fail. That appears to be the issue above. Anyway, try the manual mount, see if it works.  If it does, I'd move the IPv7 into the auto.nfs files and try again.  I have a suspicion that mDNS/Avahi is the issue.

Not that it should matter, but the options I use with NFS are: nconnect=4,proto=tcp,rw,async  In theory, NFSv4 uses tcp automatically, readwrite is the default.  async is for improved performance and nconnect added in NFSv4.1 is to provide more concurrent network connections on our faster networks, with monster CPUs.

NFS v2/v3 is from the 1990s.
NFS v4 has been around since the early 2000s.  It shouldn't need to be specified, but if there are 2 ubuntu systems involved, since around 2010, they should have negotiated NFSv4 connections and IPv6 has been supported since at least 2005.

I don't use IPv6 on my LAN at all, so I cannot test any of this, but I have tested NFSv4 and autofs with 22.04, 20.04 and all prior LTS releases. It works.
```
$ df -Th
Filesystem                      Type  Size  Used Avail Use% Mounted on
istar:/d/D1                     nfs4  3.5T  3.5T  4.4G 100% /d/D1
istar:/d/D2                     nfs4  3.6T  3.6T  3.1G 100% /d/D2
istar:/d/D3                     nfs4  3.6T  3.6T  908M 100% /d/D3

```

I have a LAN DNS server to resolve istar's IP.  Above is some mounted storage on a 20.04 system using autofs.  I think avahi/mdns is an abomination.  It has a long history of problems.

I am concerned about mounting anything from /home/ anywhere else.  Snap packages don't like NFS in /home.  I know for years, snaps and NFS didn't get along.  I believe snaps started working with NFS about 2 yrs ago, but only in very specific ways that I cannot use.  May be worth researching.

---

### Post by The Cog on 2022-10-28
That trailing %3 is not a valid part of an IP address. I'm guessing that there is a fault with whatever is resolving the hostname into an IP address.
Try the command "host computer1.local" and see what comes out.
I know nothing whatsoever about autofs - I'm just looking at a bad IP address.

---

### Post by georgesgiralt on 2022-10-29
Hello Guys,
Yesterday was a busy day. So didn't work on this. 
But today I played a little...
Provided I had a correct exports file on the nfs server allowing mount from other computers on the local network, ( a line like that in /etc/exports : /home/georges 	xxxx:xxx:xxx:xxx::/64 )
I was able to mount the NFS share if I gave the IPV6 address of the server : 
```

#mount      -t nfs       -o rw,hard,intr   [xxxx:xxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx]:/home/georges /mnt
root@computer:~# ls /mnt
 109187-01.zip	 ...........

```

But the same mount command using the mDNS name of the server gave errors .... 
```
# mount      -t nfs    -v   -o rw,hard,intr   server.local:/home/georges /mnt
mount.nfs: timeout set for Sat Oct 29 09:20:23 2022
mount.nfs: trying text-based options 'hard,intr,vers=4.2,addr=2xxx:xxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx%3,clientaddr=xxxx:xxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx'
mount.nfs: mount(2): Invalid argument
mount.nfs: trying text-based options 'hard,intr,vers=4.1,addr=2xxx:xxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx%3,clientaddr=xxxx:xxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx'
mount.nfs: mount(2): Invalid argument
mount.nfs: trying text-based options 'hard,intr,vers=4.0,addr=2xxx:xxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx%3,clientaddr=xxxx:xxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx'
mount.nfs: mount(2): Invalid argument
mount.nfs: trying text-based options 'hard,intr,addr=2xxx:xxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx%3'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 2xxx:xxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx%3 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 2xxx:xxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx%3 prog 100005 vers 3 prot UDP port 53112
mount.nfs: mount(2): Invalid argument
mount.nfs: an incorrect mount option was specified

```
As you can see, the resolver append a %3 on the IPV6 address of the NFS server. And this cause the whole mount to fail. I've checked that the IPV6 address I get to make the mount work is the same the resolver gave but without the "%3 " added...
So as always, a bug is not where one search for it. 
Now I've to devise why the resolver append this "%3" on the response ...
And all your help will be gratefully accepted ! 
Have a nice and bright day

---

### Post by georgesgiralt on 2022-10-29
Oh, and by the way : 
```

host computer1.local
Host computer1.local not found: 3(NXDOMAIN)
```

---

### Post by TheFu on 2022-10-29
Avahi and mdns are abominations.  Best to disable them and use DNS instead.  I'm 100% serious.  The /etc/nsswitch.conf file controls the order that name resolution happens.  Changes to it are immediate.

```
hosts:          files dns
```
is what I have in mine to avoid mdns issues.  Plus, I purge avahi.

---

### Post by georgesgiralt on 2022-10-29
Ah! 
Turning off Avahi and mDNS is not an option at all as I *need* them both to account for the various interface some of my computer use (2 Ethernet, one wifi, sometimes bluetooth when using my data plan) so I've to find where the bug is an correct it.

---

### Post by TheFu on 2022-10-29
> **georgesgiralt said:**
> Ah! 
Turning off Avahi and mDNS is not an option at all as I *need* them both to account for the various interface some of my computer use (2 Ethernet, one wifi, sometimes bluetooth when using my data plan) so I've to find where the bug is an correct it.

You do realize that avahi is 100% replaced for DNS by  ... er ... a DNS server, right?  Heck, many routers will do it, if you don't want to run a pi-hole with dnsmasq as a tiny DNS server for your LAN.  Plus, servers need to have static IPs for a number of reasons.

But if you don't want to have a properly managed network, that's your choice.  Expect problems.

---

### Post by georgesgiralt on 2022-10-30
Hello,
The problem is with the nfs mount command which can't handle the IPV6 address it is given. Not in Avahi/mDNS ...
See : 
```

 RFC 4007 (IPv6 Scoped Address Architecture) introduces the percent sign ("%") as a separator between an IPv6 address literal and a zone_id. It describes that a zone identifier can be numeric or a string. Therefore, we can refer to the address fe80::1 on interface eth0 as fe80::1%eth0 and (if eth0 maps to interface number 1) as fe80::1%1.
```
As the machine has 3 IPV6 addresses on the wifi interface (and 3 for every interface plugged/configured). The %3 in the end of the IPV6 address shown just tell the guy which interface to use for it's job and what address to query. 
```

ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp45s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 7c:8a:e1:7a:f2:d9 brd ff:ff:ff:ff:ff:ff
3: wlp0s20f3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether b0:60:88:f2:05:d5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.67/24 brd 192.168.0.255 scope global dynamic noprefixroute wlp0s20f3
       valid_lft 29532sec preferred_lft 29532sec
    inet6 xxxx:xxx:xxx:xxxx:382b:fe68:fd32:4eab/64 scope global temporary dynamic
       valid_lft 86079sec preferred_lft 50825sec
    inet6 xxxx:xxx:xxx:xxxx:147e:d186:1ab2:b3ed/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 86079sec preferred_lft 86079sec
    inet6 fe80::4408:5bdb:ddd7:e2ec/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
4: enx00e04c685fcb: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 00:e0:4c:68:5f:cb brd ff:ff:ff:ff:ff:ff

```

---

### Post by TheFu on 2022-10-30
Excellent catch!   Definitely open a bug.

I found 2 serverfault posts with this in it and suggested workarounds.
[https://serverfault.com/questions/841976/how-to-specify-ipv6-address-to-use-while-mounting-nfs](https://serverfault.com/questions/841976/how-to-specify-ipv6-address-to-use-while-mounting-nfs)
One suggested some settings for mdns.

Are any of the provided workarounds something to consider in your environment?

---

### Post by georgesgiralt on 2022-10-30
Hello,
I've no time for submitting a bug. Life is too short. And it will remind my former work too much (I'm a retired IT engineer). 
For now, I'm happy with this line in my /etc/nsswitch.conf :
```

hosts:          files mdns4 [NOTFOUND=return] dns myhostname
```
It makes ipv4 resolution first and reverse lookup to function properly. It's all I want for now.
I can change network type (wired, wifi, or 4G GSM) and still get access to the NFS/autofs mount I want/need. 
I'll revert to my previous task....
Have a nice day.
Edit : I've found that the mdns setting can take : mdns, mdns_minimal, mdns4, mdns4_minimal, mdns6, mdns6_minimal.... I bet some of them are aliases. The minimal keyword makes reverse dns lookup ineffective (arp -a render nothing for a given IP addr)

---

### Post by TheFu on 2022-10-30
'arp -a' is deprecated.  'ip neighbor' is the replacement.  All the ifupdown tool code hasn't been supported since 2011.  The ip tools seem to have extra options to get the same and sometimes much more information.  Sadly, they didn't reproduce 'route -n' with pretty columns that are easy to read.

---

### Post by georgesgiralt on 2022-10-30
> **TheFu said:**
> 'arp -a' is deprecated.  'ip neighbor' is the replacement.  All the ifupdown tool code hasn't been supported since 2011.  The ip tools seem to have extra options to get the same and sometimes much more information.  Sadly, they didn't reproduce 'route -n' with pretty columns that are easy to read.

And ip neighbor does not give any interesting information. What is the hostname of this IP addr ? which is the sole information we need when doing an arp table lookup.... (and accessory checking that reverse DNS lookup is working which is VERY important information for security purposes)
People nowadays are more interested in making round corners to the windows displayed on their screen or making nice animations when iconizing a window than understanding how and for what some code has been written and make it work.... 
Sorry for the rant. I'll take my pills and go to bed.

---

