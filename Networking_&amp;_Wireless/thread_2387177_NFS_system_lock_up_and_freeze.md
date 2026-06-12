---
title: "NFS system lock up and freeze"
date: 2018-03-15
forum: Networking &amp; Wireless
---

### Post by jbamford92 on 2018-03-15
Howdy folks,

I have a problem with NFS shares on my Desktop. When copying files from my servers its fine but copying files to the server causes a total system lock up or the transfers stops and keeps starting. Im using Ifenslave but i know its not just a Intel Ethernet issue because my Laptop which uses realtek has the same problem. Im using NFS utils with Ubuntu 16.04 on both of my Clients and FreeNAS for my Server. Ive tried with both Jumbo enabled and Disabled. But this issue where the whole system locks up resulting in holding the power button to unlock the system is annoying. 

Would anyone have any ideas on how to fix the problem?

Thanks.

Jack.

---

### Post by SeijiSensei on 2018-03-16
Try using "async" as an option. You'll be at risk of data loss if there's a power outage. My server is on a UPS so that's not really an issue for me.

---

### Post by jbamford92 on 2018-03-16
> **SeijiSensei said:**
> Try using "async" as an option. You'll be at risk of data loss if there's a power outage. My server is on a UPS so that's not really an issue for me.


Hi,

Thanks for your reply. Im already using aSync. Small files like documents, pictures etc are fine but anything over 1GB causes either the transfer to freeze or the System to total lockup. Using the Client to Copy from one Server to the other is perfectly fine via NFS but copying from either Ubuntus Boot Drive or Internal Storage drive is the issue. 

Now ive looked at my kern.log and its shows this,

```
10.528129] IPv6: ADDRCONF(NETDEV_CHANGE): bond0: link becomes readyMar 16 04:53:33 Violets-Desktop kernel: [   12.800500] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Mar 16 04:53:33 Violets-Desktop kernel: [   12.800677] NFSD: starting 90-second grace period (net f00000a9)
Mar 16 04:53:33 Violets-Desktop kernel: [   12.856588] FS-Cache: Loaded
Mar 16 04:53:33 Violets-Desktop kernel: [   12.918952] FS-Cache: Netfs 'nfs' registered for caching
Mar 16 04:53:36 Violets-Desktop kernel: [   15.377013] random: crng init done
```

This is what i have in /etc/fstab/

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=d401fe65-7112-4f84-a9c9-24a97ca6c8f5 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=D404-4B5B  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=e2c547ad-0c12-49ce-8a43-47a423c1428d none            swap    sw              0       0


/dev/sdb1    /home/violetdragon/Storage    ext4    defaults    0    1


192.168.1.1:/mnt/tank/Storage /home/violetdragon/Storage/Server nfs intr,async,nfsvers=3,bg,actimeo=0 tcp 1800 00
```

Ive tried both with FreeNAS & Linux Ubuntu with NFS Server running and still the same problem. The Linux NFS/SAMBA Server uses 10/100 which works perfect fine without a lockup or freezes on the transfer.

This is what im using with iFenslave for the HP NC630T. All machines have the HP NC630T and having the same problem, Although my Laptop which uses Realtek has the same problem.

```
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
auto eth0
iface eth0 inet manual
bond-master bond0
        pre-up /sbin/ip link set dev $IFACE mtu 1500
        post-up /sbin/ethtool -G $IFACE rx 4096
        post-up /sbin/ethtool -G $IFACE tx 4096


# Second NIC
auto eth1
iface eth1 inet manual
        bond-master bond0
        pre-up /sbin/ip link set dev $IFACE mtu 1500
        post-up /sbin/ethtool -G $IFACE rx 4096
        post-up /sbin/ethtool -G $IFACE tx 4096


# Virtual NIC
auto bond0
iface bond0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        dns-nameservers 192.168.1.254
        bond-mode balance_rr
        bond-miimon 2000
        bond-slaves eth0 eth1
        pre-up /sbin/ip link set dev $IFACE mtu 1500
        pre-up /sbin/ip link set dev $IFACE address 00:1b
```

Heres what ive tried, Mounting the NFS Shares on the Internal Drive which is a 120GB SSD i have for Storage, Ive tried different buffer sizes within the /etc/fstab auto mount but the same problem, I tried NFS Server on the clients instead of nfs-common also the same problem i tried removing iFenslave completely without bond0 and a fresh install. Copying from the Servers to the Clients is perfectly fine but copying too with NFS from the internal boot drive or storage drive is the real problem here.

---

### Post by TheFu on 2018-03-16
I can only suggest that you simplify and test.  Keep doing that until the cause is determined.

BTW, you can remove these lines from the interfaces file.  Unnecessary.  address, netmask, and gateway are sufficient.
```

        network 192.168.1.0
        broadcast 192.168.1.255
```

You didn't mention it, but I assume your network hardware supports jumbo frames and link aggregation standards?
 IEEE 802.1AX or the older IEEE 802.3ad?

My first thought was that it was a permissions issue, but that should cause an error 13.  How is the uid/gid mapping handled?

---

### Post by jbamford92 on 2018-03-16
> **TheFu said:**
> I can only suggest that you simplify and test.  Keep doing that until the cause is determined.

BTW, you can remove these lines from the interfaces file.  Unnecessary.  address, netmask, and gateway are sufficient.
```

        network 192.168.1.0
        broadcast 192.168.1.255
```

You didn't mention it, but I assume your network hardware supports jumbo frames and link aggregation standards?
 IEEE 802.1AX or the older IEEE 802.3ad?

My first thought was that it was a permissions issue, but that should cause an error 13.  How is the uid/gid mapping handled?

Hi.

Thanks for your reply. Load balancing is enabled on the switch via trunk & VLANs same with Jumbo Frames.

However i found something very interested here. Copying from a Solid State drive causes the lockup or link to Freeze however copying from a 7200RPM spinning disk is perfectly fine. Ive got both of my client machines in bits atm trying to solve this problem. 

The Switch i have is a HP Procurve 2510G i have tried both LACP and Trunk but still have the same problem. The switch supports IEEE 802.3ad link to the switch if you want to check it out.

I have tried multiple different SSDs some are kinda okay and others causes a huge issue with the instant lock up of the System.

Not quite sure what you mean by How is the uid/gid mapping handled?

Thanks.

Jack

---

### Post by TheFu on 2018-03-16
NFS userid/groupid mapping is handled strictly by the numbers. I've never used storage systems that didn't get their userids from external providers - usually LDAP.  

Have you looked at the NICs for issues?  I know that some NICs have shown issues with NFS and VoIP traffic. There are/were bugs in launchpad.   For those, it wasn't limited to just NFS traffic, but other sorts of traffic too. ZFS was mentioned as well as was avahi and name resolution issues.  One guy put in an /etc/hosts entry and that fixed everything (he claimed). Another person switched from UDP to TCP and claims that solved it.

Also, what do the other logs show? Anything bad?

---

### Post by jbamford92 on 2018-03-16
> **TheFu said:**
> NFS userid/groupid mapping is handled strictly by the numbers. I've never used storage systems that didn't get their userids from external providers - usually LDAP.  

Have you looked at the NICs for issues?  I know that some NICs have shown issues with NFS and VoIP traffic. There are/were bugs in launchpad.   For those, it wasn't limited to just NFS traffic, but other sorts of traffic too. ZFS was mentioned as well as was avahi and name resolution issues.  One guy put in an /etc/hosts entry and that fixed everything (he claimed). Another person switched from UDP to TCP and claims that solved it.

Also, what do the other logs show? Anything bad?

All the logs are showing is that NFS Cache i dont know what to do. But using a Spinning disk for the mount seems to help the problem.

The Lan Cards im using are HP NC360t & Realtek which is in my Laptop which is a RTL8111.

---

### Post by TheFu on 2018-03-16
I use NFS here on a GigE network ... ALL-THE-TIME.  To/from SSD storage.  My NFS servers all use Intel PRO/1000 NICs.  I'm a bigot that way.
Can you try a different protocol - not NFS - see if there is an issue?

---

### Post by jbamford92 on 2018-03-16
> **TheFu said:**
> I use NFS here on a GigE network ... ALL-THE-TIME.  To/from SSD storage.  My NFS servers all use Intel PRO/1000 NICs.  I'm a bigot that way.
Can you try a different protocol - not NFS - see if there is an issue?

SMB works but the speeds are dreadful. Im kinda getting a bit further. I changed from trunk to lacp and im not seeing the system lockup like i was. But transfers from a SSD still have the pause. I think its due to a IO wait on the SSD but a 7200RPM disk is perfectly fine.

This is what ive done to /etc/network/interfaces.

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto eth0
iface eth0 inet manual
bond-master bond0
        pre-up /sbin/ip link set dev $IFACE mtu 1500
        post-up /sbin/ethtool -G $IFACE rx 4096
        post-up /sbin/ethtool -G $IFACE tx 4096

# Second NIC
auto eth1
iface eth1 inet manual
        bond-master bond0
        pre-up /sbin/ip link set dev $IFACE mtu 1500
        post-up /sbin/ethtool -G $IFACE rx 4096
        post-up /sbin/ethtool -G $IFACE tx 4096

# Virtual NIC
auto bond0
iface bond0 inet static
        address 192.168.1.2
        netmask 255.255.255.
        gateway 192.168.1.254
        dns-nameservers 192.168.1.254

# bond0 uses standard IEEE 802.3ad LACP bonding protocol
    bond-mode 4
    bond-miimon 100
    bond-lacp-rate fast
    bond-slaves eth0 eth1
    pre-up /sbin/ip link set dev $IFACE mtu 1500
    pre-up /sbin/ip link set dev $IFACE address 00:1b:78:59:7c:60
    bond-downdelay 0
    bond-updelay 0
    bond-xmit_hash_policy 1
```

---

### Post by TheFu on 2018-03-17
Is netmask 255.255.255.  a valid entry for netmask?

Manpage  says:```

              netmask mask
                     Netmask (dotted quad or CIDR)
```
I would expect 255.255.255.0 is correct.  I know other config files work fine without the trailing numbers, just don't know about the interfaces file.

Can you test plain FTP?  Testing only, it is useful.  I'd never use it for any other reason.  Just trying to figure out if it is the protocol, network stack, network options, HW or something else.

Also, would be really good to remove the link aggregation too.

Simplify and test.

---

### Post by jbamford92 on 2018-03-17
> **TheFu said:**
> Is netmask 255.255.255.  a valid entry for netmask?

Manpage  says:```

              netmask mask
                     Netmask (dotted quad or CIDR)
```
I would expect 255.255.255.0 is correct.  I know other config files work fine without the trailing numbers, just don't know about the interfaces file.

Can you test plain FTP?  Testing only, it is useful.  I'd never use it for any other reason.  Just trying to figure out if it is the protocol, network stack, network options, HW or something else.

Also, would be really good to remove the link aggregation too.

Simplify and test.

Ive removed link aggregation in my testing but makes no difference. It makes transfers a lot slower. I believe its something to do with the SSDs timing out. When using just your average hard drive 7200RPM i dont see the activity like i do with a SSD. When the transfer stops the hard activity light goes out but the link stays up. Maybe its something to do with the disks in my server trying to catchup with the SSD.

---

### Post by TheFu on 2018-03-18
I've never seen anything  like this, but my SSD experience is fairly limited.

I'd systematically check each component involved, keeping track of peak performance for each part; disk, network, storage, controllers.  I'd use iperf3, bonnie++, iostat and sar. Facts should nail down where the HW or driver issue is quickly.  Guessing isn't all that useful unless you are very lucky.

Google finds lots of people with NFS issues.  They all seem to assume that NFS **is** the issue when  they start, and a few times that turned out to be true, but not always.  "NFS cache" was the search term.

---

### Post by jbamford92 on 2018-03-19
> **TheFu said:**
> I've never seen anything  like this, but my SSD experience is fairly limited.

I'd systematically check each component involved, keeping track of peak performance for each part; disk, network, storage, controllers.  I'd use iperf3, bonnie++, iostat and sar. Facts should nail down where the HW or driver issue is quickly.  Guessing isn't all that useful unless you are very lucky.

Google finds lots of people with NFS issues.  They all seem to assume that NFS **is** the issue when  they start, and a few times that turned out to be true, but not always.  "NFS cache" was the search term.

Hi Sorry for a late reply. 

I downloaded a utility which allows me to see the Disks Read and Write. Ive noticed something very interesting when Copying to the Server from the SSD the Read goes to 0 read but the Networks Utilization is showing that both links are totally saturated. Even tho the copying has stalled something i wasnt expecting if you ask me.

Is there anyway i can attach a recorded screen video?

---

### Post by TheFu on 2018-03-19
SSDs are fast.  10-1000x faster than spinning disks.  Some SSDs are faster than GigE networks.  
Facts are critical.

I don't need a video (and won't watch one).  I usually won't click on images either. Text. Please.
> 
I'd systematically check each component involved, keeping track of peak performance for each part; disk, network, storage, controllers. I'd use iperf3, bonnie++, iostat and sar. Facts should nail down where the HW or driver issue is quickly. Guessing isn't all that useful unless you are very lucky.

---

