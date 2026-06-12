---
title: "Samba Server side copying"
date: 2023-12-07
forum: Networking &amp; Wireless
---

### Post by biojo on 2023-12-07
Does unbuntu support this "server side copying"

I have a NAS server and when I copy say a 10gb file in windows the speeds are 500mb/sec as it doesnt go through the laptops wireless connection, but shows the copying dialog box

when try on ubuntu it does 15mb/sec as its reciving and sending the file

---

### Post by TheFu on 2023-12-07
[https://wiki.samba.org/index.php/Server-Side_Copy](https://wiki.samba.org/index.php/Server-Side_Copy)  

Basically, it depends on a number of factors, which that link outlines.  It isn't an "ubuntu" specific question, since there are choices in your setup that impact whether it can or cannot work regardless of the OS or OS release .... which you didn't say.  For example, not all versions of MS-Windows support it.  The underlying file system can aid or limit the support. Other things.

So, if you want it to work, you'll need to line up the supported SW stack and file system choices.

If you want to just copy files locally, why not ssh into the system and do it quickly on the system with the files? I get that changing how you work can be seen as a hassle. OTOH, it is an opportunity to do it the "Unix way".    Of course, if a mv, not a cp is desired, and the source/target locations are within the same file systems, then the move is nearly instantaneous, regardless of file size. It just connects the inode to a new parent. It is extremely fast.  Of course, moving across file systems is effectively a cp to the new and rm from the old, so no savings there.

---

### Post by biojo on 2023-12-08
ok so the NAS server is OMV6 with multiple shares and hard drives

In windows 10/11 I mapped certain shares, and i could copy betweeen one shared location to another FAST

In ubuntu 22.04 im in the GUI not terminal, and i have mounted shared e.g.

smb://nas/backup
smb://nas/tempdrive

I just want if possible to copy from one share to other like in windows for it to be server side

Im not copying anything to local hard drive, that is what it is when it comes to speed of network, its just the server side copying I want working

---

### Post by TheFu on 2023-12-08
Well, the list of required software for the client is in the link I already posted.  Since it works on MS-Win10+, I'd just look at the Linux client to ensure it meets those requirements.
For a Linux client, the link says this: 
> 
The Linux Kernel CIFS client includes support for issuing SMB2 FSCTL_SRV_COPYCHUNK_WRITE server-side copy requests. This feature can currently only be utilised by issuing a special CIFS_IOC_COPYCHUNK_FILE ioctl, as done by cloner in the xfstests Git repository.

Linux Kernel support for FSCTL_DUPLICATE_EXTENTS_TO_FILE was added with kernel version 4.2, and can be issued via cp --reflink on supported systems with SMB3+ mounts.


Later, is says:

> Limitations:
    The client must support, and issue SMB2 FSCTL_SRV_COPYCHUNK server-side copy requests.

So the answer would be to verify that 
a) you have at least the minimum level of samba-client software installed.
b) the specific program you are using meets the other requirements.

You'll need to look up that information for your specific system and the GUI tool being used.  There are lots of different file managers on Linux. Perhaps some support what you seek? I googled for that specific capability and didn't find any good information.

Most Linux GUI file managers will use gvfs and gio API to handle remote "fake-mounts".  There's a bug in gvfs to support server-side copies [https://gitlab.gnome.org/GNOME/gvfs/-/issues/286](https://gitlab.gnome.org/GNOME/gvfs/-/issues/286) , but that bug is listed as "superseded" and falls down a hole that you can follow.

[https://arstechnica.com/civis/threads/ubuntu-use-server-side-file-operations-when-moving-files-on-windows-share.1455731/](https://arstechnica.com/civis/threads/ubuntu-use-server-side-file-operations-when-moving-files-on-windows-share.1455731/) says that NFS support it.  I tested it on my NFS systems here by copying a 1.2GB file locally and over an NFS mount using 'cp'.

**Local copy:**
```
real    0m**0.612s**
user    0m0.000s
sys     0m0.609s

```
**NFS copy:**
```
real    0m**21.020s**
user    0m0.004s
sys     0m0.796s
```

I did another test from a newer NFS client OS.
```
real    0m**3.162s**
user    0m0.000s
sys     0m1.369s
```

If it doesn't work using 'cp' between (2) 20.04 Ubuntu servers that are GigE connected, it won't work using a GUI program either.  Far from ideal and I find it a bit surprising.
That last test was using 25Gbps networking and the client was a Linux Mint 21.2 (based on 22.04) system.  All connections are NFS v4.2.  So, faster networking provides faster copies is all that says to me. Not exactly useful.

Because I have interest, seems that the coreutils library capability for NFS server-side copy was added in v9 of coreutils.  All my Ubuntu/Debian systems are on v8.x of coreutils, but I've seen reports from someone who compiled the newer version and server-side copy worked - for NFS.  Looks like coreutils v9.1.x is in Debian 12 (released last June), so I'd be really surprised of Ubuntu 24.04 didn't include it.  I don't touch non-LTS versions of Ubuntu.   This is for NFS and doesn't help with CIFS, sorry.

That same thread says that  KDE Framework 5.88 onwards implements the needed update for NFS too.  That would be the file manager in KDE or LXQt, I suppose.   I don't use either.

I don't have CIFS/Samba running anywhere, so I'm unwilling to actually test that. Maybe someone else will?  Just be prepared to know the exact versions of the exact programs being used.

---

### Post by Morbius1 on 2023-12-08
> In ubuntu 22.04 im in the GUI not terminal, and i have mounted shared e.g.

smb://nas/backup
smb://nas/tempdrive

From what I can comprehend from the samba wiki this is only possible from a cifs mount - as in mount.cifs. What you are using is a samba client mount. It also appears to be a SMB2+ attribute which a mount.cifs uses by default.

It also talks about version 4.2 of the Linux Kernel where mount.cifs lives and Ubuntu 22.04 doesn't run with that kernel level.

My suggestion is to do a cifs mount of these two shares and see if things improve:

sudo mount -t cifs //nas/backup /mountpoint1 -o username=xxx,password=yyy,uid=1000
sudo mount -t cifs //nas/tempdrive /mountpoint2 -o username=xxx,password=yyy,uid=1000

---

### Post by biojo on 2023-12-08
cheers, my nas does supporrt NFS3 to 4.2 so in theory if that does it, I could enable that for each share

ok so installed nfs-common and used this in fstab

192.168.0.115:/export/Media /mnt/Media   nfs4.2 auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0

but still dont get server side copy, is this because of coreultils not been ver9, will this likely be upgraded on 22.04lts?

---

### Post by SeijiSensei on 2023-12-08
If you can use SSH to open a terminal on the NAS, I'd do the copy that way.

NFS will also route the copy through the client.

---

### Post by TheFu on 2023-12-08
> **SeijiSensei said:**
> If you can use SSH to open a terminal on the NAS, I'd do the copy that way.

NFS will also route the copy through the client.

coreutils v9.1.x is in Debian 12 and provides server-side copy for NFSv4.2 mounts.  coreutils v8.x doesn't support it, which is what 22.04 and earlier Ubuntu have.
I'm looking forward to 24.04 having coreutils v9.x, though most of my use wouldn't gain anything.

---

### Post by biojo on 2023-12-09
> **SeijiSensei said:**
> If you can use SSH to open a terminal on the NAS, I'd do the copy that way.

NFS will also route the copy through the client.

Yeah the NAS has SSH and although I could use it, im not that quick / confident doing it

The quickest way for me at min is to open the rdp to the Windows10 VM and copy and paste.

---

### Post by biojo on 2023-12-09
> **TheFu said:**
> coreutils v9.1.x is in Debian 12 and provides server-side copy for NFSv4.2 mounts.  coreutils v8.x doesn't support it, which is what 22.04 and earlier Ubuntu have.
I'm looking forward to 24.04 having coreutils v9.x, though most of my use wouldn't gain anything.


I just presumed ubuntu would have had it, does that mean untill then SMB also wont?  untilll core utils

I did look at installing 23.10 but I wanted LTS, Im not used to ubuntu release dates, so will 24.04 be released next year? and if so is there a month they do?

is it a straight upgrade when it is or does it have to be freshly installed?

---

### Post by TheFu on 2023-12-09
> **biojo said:**
> I just presumed ubuntu would have had it, does that mean untill then SMB also wont?  untilll core utils

I did look at installing 23.10 but I wanted LTS, Im not used to ubuntu release dates, so will 24.04 be released next year? and if so is there a month they do?

is it a straight upgrade when it is or does it have to be freshly installed?

Samba has nothing to do with 'coreutils'.  You are better off using NFS, which is the native way that Unix-like OSes share files.  It provides native UNIX permissions, that's an important aspect of any file server.

It isn't an Ubuntu thing. It is a Gnu coreutils thing.  Remember, Linux is thousands of small software projects building something. Canonical sponsors a few projects, but not the vast majority that are included in their distribution.  Samba is a separate project that reverse engineered the CIFS protocol, initially with very little help from MSFT.  MSFT has been helping the samba team, very occasionally, but hardly full time for about the last decade.

If you have a Windows VM running on the file server, then I showed the performance of a 25 Gbps NFS connection, which was a VM running on the same physical machine as the storage.  The only trick is the ensure that VM uses virtio drivers for networking and storage.  I don't know if MSFT does that by default or what hypervisor you are using, but I know that KVM supports virtio.  Inside the VM, you just need to load the virtio drivers.  Last time I did it, Redhat provided those.  For Linux VMs, the virtio drivers should be there by default and provided you setup the VM to use them, you should see a 25+x performance improvement.

---

### Post by SeijiSensei on 2023-12-09
The next LTS release, 24.04, will be available in April.

---

### Post by TheFu on 2023-12-09
There is a clear meaning to the Ubuntu version numbers.  For example, "24.04"

24 = 2024, the year
04 = April, the month

So 24.10 will be released October of 2024.   October releases are NEVER LTS (well, there was one exception with 12.10 because 12.04 really sucked).
16.04 was released 2016, April.

---

### Post by biojo on 2023-12-10
cheers,  I only recently started using NFS as the new NAS supported it and other devices on network are on debian. It just took me a bit to realise it needed CIDR set to each machine to allow them access and not just simple IPs

nice one, aprils not too long to wait

yeah the KVM runs VM with virtio drivers, but as its Windows 10/11 it shows copy speeds NAS to same NAS as 300-500MB/sec on the SSDs

---

### Post by TheFu on 2023-12-10
> **biojo said:**
> cheers,  I only recently started using NFS as the new NAS supported it and other devices on network are on debian. It just took me a bit to realise it needed CIDR set to each machine to allow them access and not just simple IPs

nice one, aprils not too long to wait

yeah the KVM runs VM with virtio drivers, but as its Windows 10/11 it shows copy speeds NAS to same NAS as 300-500MB/sec on the SSDs

I don't use CIDR subnet specs in my exports.  I actually list specific clients which are allowed access by name.
```
/d/D1   nextcloud-lxd(ro,async,root_squash,no_subtree_check,fsid=1)
/d/D1           deneb(rw,async,root_squash,no_subtree_check,fsid=1)
/d/D1           r-pi3(rw,async,root_squash,no_subtree_check,fsid=1)
/d/D1         romulus(rw,async,root_squash,no_subtree_check,fsid=1)
/d/D1           hadar(rw,async,root_squash,no_subtree_check,fsid=1)
/d/D1             pi4(rw,async,root_squash,no_subtree_check,fsid=1)
#
/d/D2 nextcloud-lxd(ro,async,root_squash,no_subtree_check)
/d/D2         deneb(rw,async,root_squash,no_subtree_check) 
/d/D2         hadar(rw,async,root_squash,no_subtree_check) 
/d/D2           rpi(rw,async,root_squash,no_subtree_check) 
/d/D2       romulus(rw,async,root_squash,no_subtree_check) 
/d/D2         r-pi3(rw,async,root_squash,no_subtree_check) 
/d/D2           pi4(rw,async,root_squash,no_subtree_check)
....

```
My LAN has DNS.  There's no reason to allow every IP on the same subnet access to NFS, so I don't.  The other 20 or so devices don't get access.  I suppose I could control access using the old tcp_wrappers method in hosts.allow and hosts.deny, but with inetd/xinetd unused, only specific daemons that build in support for tcp_wrappers support it anymore. [https://en.wikipedia.org/wiki/TCP_Wrappers](https://en.wikipedia.org/wiki/TCP_Wrappers)  That's how we did service protection before real firewalls were provided and worked without huge system overhead. TCP_Wrappers is still on our systems ... and some services still support it.  To see which things installed on your system can use libwrap, run
```
apt-cache rdepends libwrap0
```
When I do, I see ... well, lots of things, including ....
```
...
  openssh-server
  nfs-kernel-server
  nfs-common
...

```  So, if you do open the entire subnet to your NFS server, it would be smart to setup the hosts.deny and hosts.allow to limit the exact systems  that can have access, at least until you setup mandatory Kerberos authentication for NFS between the clients and server systems.

I don't see smb in that list, but that could be simply because I don't have that installed on my systems.  I know the smbd.conf file does have the ability to limit subnets that can access the smbd/cifs server. I've used those. I'd be surprised if samba didn't have built-in support for tcp_wrappers. Very surprised.

There's always more to know.

---

### Post by biojo on 2023-12-10
Im not allowing all IPs access to NFS shares, router has MAC to IP binding,  then the NFS allows access is either TV boxs IP/32 or the Laptops IP/32 certain things only get RO access but laptop has full RW

---

### Post by biojo on 2023-12-13
ok so installed ubuntu 23.10 on a VM, fstab set to the NFS mount as this has coreutils 9, 

did a copy and paste in GUI still only 65MB a sec, so looks to be using the network card

Whats the cp command to test, and show speeds

---

