---
title: "NFS shares will not mount on client"
date: 2020-08-26
forum: Networking &amp; Wireless
---

### Post by cscj01 on 2020-08-26
I am on Ubuntu 18.04 x64 using an NFS V3 configuration.

I had a system disk crash and had to restore from a backup.  Everything is fine except my NFS shares.  I have a LAN wiith two PC's on it.  The NFS host is named cp2.  I have been running this setup for years (I can't remember when I started, but it must have been at least 12.04 and was probably earlier).  After the restore of my backup, I can not mount my NFS shares.  First I issue ```
sudo exportfs -ra
sudo systemctl restart nfs-kernel-server
```on the NFS host.  Then I issue```
sudo mount -all
``` on the client PC.  In the past this would mount the shares and all was okay.  Now when I issue```
sudo mount -all
```I get the following message```
mount.nfs: Connection timed out
```There has been no change to my network since the backup was taken.  If I try to ping cp2 from the client, I get```
Temporary failure in name resolution
```I can ping URL's successfully, both by name and by address, i.e., nnn.nnn.nnn.nnn.  I am at a loss as what to do next.

---

### Post by SeijiSensei on 2020-08-27
The simplest solution for the name resolution problem is to add an entry in /etc/hosts like this:

```
10.10.10.10        cp2
```

replacing 10.10.10.10 with the approrpriate IP address.

Try running mount with the "-v" (verbose) switch.

```
sudo mount -v etc.
```

If this still doesn't solve the problem, let's see a representative NFS entry from /etc/fstab.

---

### Post by TheFu on 2020-08-27
Did you also restart the rpcbind service first?

I ask because a few weeks ago, my 16.04 NFS clients and NFS servers had troubles that seemed similar after an update. I never figured out the exact issue, but restarting rpcbind before nfs-server made it work.

You can always use the IP address for NFS mounts, provided the server allows that.

May be helpful to see the "exports" lines on the server and however you mount on the client.  I use **autofs** for NFS on the clients, since fstab isn't always good with unavailable storage devices and the systemd-automount tools don't seem to remove unused mounts.

---

### Post by cscj01 on 2020-08-27
> **SeijiSensei said:**
> The simplest solution for the name resolution problem is to add an entry in /etc/hosts like this:

```
10.10.10.10        cp2
```

replacing 10.10.10.10 with the approrpriate IP address.

Try running mount with the "-v" (verbose) switch.

```
sudo mount -v etc.
```

If this still doesn't solve the problem, let's see a representative NFS entry from /etc/fstab.

I added the address to the /etc/host file.  I then ran the mount command as you suggested.  Here are the results:```
sudo mount -v -all
[sudo] password for butch: 
none                     : ignored
/media/Data_Three        : already mounted
/media/Data_Two          : already mounted
/media/Data_One          : already mounted
/media/Data              : already mounted
/media/butch/Ubuntu_Data_Back: already mounted
mount.nfs: timeout set for Thu Aug 27 12:50:06 2020
mount.nfs: trying text-based options 'vers=3,addr=192.168.1.102'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: trying text-based options 'vers=3,addr=192.168.1.102'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: trying text-based options 'vers=3,addr=192.168.1.102'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: trying text-based options 'vers=3,addr=192.168.1.102'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: trying text-based options 'vers=3,addr=192.168.1.102'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: trying text-based options 'vers=3,addr=192.168.1.102'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: trying text-based options 'vers=3,addr=192.168.1.102'
mount.nfs: prog 100003, trying vers=3, prot=6
^Z
[3]+  Stopped                 sudo mount -v -all

```I then tried to ping cp2 using its address and received the following:```
ping 192.168.1.102
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
From 192.168.1.162 icmp_seq=1 Destination Host Unreachable
From 192.168.1.162 icmp_seq=2 Destination Host Unreachable
From 192.168.1.162 icmp_seq=3 Destination Host Unreachable
From 192.168.1.162 icmp_seq=4 Destination Host Unreachable
From 192.168.1.162 icmp_seq=5 Destination Host Unreachable
From 192.168.1.162 icmp_seq=6 Destination Host Unreachable
^Z
[5]+  Stopped                 ping 192.168.1.102

```Finally, I tried the following:```
nmap -Pn 192.168.1.102

Starting Nmap 7.60 ( [https://nmap.org](https://nmap.org) ) at 2020-08-27 13:13 EDT
Nmap scan report for cp2 (192.168.1.102)
Host is up (0.047s latency).
All 1000 scanned ports on cp2 (192.168.1.102) are filtered

Nmap done: 1 IP address (1 host up) scanned in 5.89 seconds

```I also restarted rpcbind on the server in the order that TheFu suggested.  So all I have ascertained (as far as my limited knowledge goes) to this point is that my NFS server is on the network, but it is unreacheable.

One final point.  I checked /run/resolvconf/resolv.conf, and it contains the following:```
 Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.

nameserver 127.0.0.53
search triad.rr.com[/QUOTE]  triad.rr.com is an old URL.  How can I change this?  I also ran the following:[QUOTE]systemd-resolve --status
Global
          DNS Domain: triad.rr.com
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

Link 3 (eno1)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no

Link 2 (enp6s0)
      Current Scopes: DNS
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
         DNS Servers: 192.168.1.1
                      2606:a000:1010:c353:6238:e0ff:feb4:fd8
          DNS Domain: ~.
                      triad.rr.com
```So, where to next?

---

### Post by TheFu on 2020-08-27
```
ping 192.168.1.102
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
From 192.168.1.162 icmp_seq=1 **[COLOR="#FF0000"]Destination Host Unreachable[/COLOR]**
From 192.168.1.162 icmp_seq=2 Destination Host Unreachable
From 192.168.1.162 icmp_seq=3 Destination Host Unreachable
``` 

**ping 192.168.1.102** is NOT working!  You have a network connectivity issue on 1 or both systems.  Nothing to do with NFS. NFS is just a symptom.

---

### Post by cscj01 on 2020-08-27
> **TheFu said:**
> ```
ping 192.168.1.102
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
From 192.168.1.162 icmp_seq=1 **[COLOR="#FF0000"]Destination Host Unreachable[/COLOR]**
From 192.168.1.162 icmp_seq=2 Destination Host Unreachable
From 192.168.1.162 icmp_seq=3 Destination Host Unreachable
``` 

**ping 192.168.1.102** is NOT working!  You have a network connectivity issue on 1 or both systems.  Nothing to do with NFS. NFS is just a symptom.
Okay, I found the problem.  For some reason (and I do not know why) the address of cp2 is now 192.168.1.111.  The address is manual, not automatic, so DHCP is not a factor.  Once I changed the hosts file and fstab > sudo mount -all mounted the two NFS shares.  The 192.168.1.111 seems familiar, so I must have set that after I took the last backup.  I have learned several lessons with this issue.  Thanks for your suggestions and observations.  One thing I need to do is back up the system drive more frequently.  I'll close this thread as solved with many thanks to you.

---

### Post by TheFu on 2020-08-27
> **cscj01 said:**
>   I have learned several lessons with this issue.  Thanks for your suggestions and observations.  One thing I need to do is back up the system drive more frequently.  I'll close this thread as solved with many thanks to you.

Team  effort. If you hadn't posted the commands AND output, we would probably have wasted a tonne of time on completely unrelated stuff.  We all have blinders from time to time.  Thanks for not making getting data like a dentist trying to find and pull a rotten tooth.

I suspect you are using dhcp still, btw.  Static IPs don't change. With netplan, it is easy to leave dhcp enabled and not realize it.  Best not to leave network-manager in control of anything.

---

### Post by scottbomb on 2020-09-20
I don't know why, but the folks at Canonical have really screwed up name resolution. Every time I do an install of focal, I now have to do the following:

cd /etc
sudo rm -rf /etc/resolv.conf
sudo ln -s /run/systemd/resolve/resolv.conf

then, I go into hosts and define all of the machines on my lan, like this:

192.168.1.2 main
192.168.1.3 blackbox
192.168.1.4 whitebox

...etc.

Hope that helps.

---

