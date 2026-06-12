---
title: "Samba/CIFS performance - am I being unrealistic?"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by mike503 on 2008-02-08
I have two Linux machines on the same gigE switch.

I have mounted them back and forth and copied files, and the most I can get is 27 megabytes/sec. These have gigabit interfaces and I have enabled jumbo frames of different sizes up to 9000 on both sides, also tweaked the smb.conf settings and such, and 27 or so is the fastest I can get it.

Am I being unrealistic to think I can get better?

I was able to transfer at 118MB/sec roughly using FTP (it might have even been SCP with the encryption overhead) on some servers I ran before. So I know Linux can almost hit the theoretical ~ 125MB/sec limit.

Any help is appreciated. I am Googled to death now...

Here's the output from one of the sides:

root@local:~# ethtool -k eth0
Offload parameters for eth0:
Cannot get device udp large send offload settings: Operation not supported
rx-checksumming: on
tx-checksumming: on
scatter-gather: on
tcp segmentation offload: on
udp fragmentation offload: off
generic segmentation offload: off

---

### Post by ian dobson on 2008-02-08
Hi,

The CIFS network protocol isn't that efficient and 27 megabytes/sec isn't that bad. I would be happy to get that at work to the main windows server.

Maybe have a look at using NFS if windows compatibility isn't that important.

How are you testing? 

Regards
Ian Dobson

Edit: Also have a look here [http://samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html) for tuning options

---

### Post by lansalot on 2008-02-08
What tweaks have you implemented in smb.conf ?

Disks slow or overly-fragmented perhaps ?

Also, at the risk of asking a stupid question, does your switch support jumbo frames ?

---

### Post by Spenzer4Hire on 2008-02-08
I have had similar results with Samba.  Switching to NFS doubled my speeds.  NFS is pretty easy to setup if you don't have to support Windows.

---

### Post by mike503 on 2008-02-08
tweaks from various places:

# [http://www.techworld.com/opsys/features/index.cfm?featureid=493](http://www.techworld.com/opsys/features/index.cfm?featureid=493)
read raw = no
write raw = yes

# [http://www.informit.com/library/content.aspx?b=red_hat_linux7&seqNum=159](http://www.informit.com/library/content.aspx?b=red_hat_linux7&seqNum=159)
wide links=yes
getwd cache=yes

# [http://groups.google.com/group/mailing.unix.samba/browse_thread/thread/f7fe67d3d8af99c0](http://groups.google.com/group/mailing.unix.samba/browse_thread/thread/f7fe67d3d8af99c0)
stat cache = yes
strict sync = no
use sendfile = yes
large readwrite = yes
oplock contention limit = 5
oplock break wait time = 100

# [http://ubuntuforums.org/archive/index.php/t-219510.html](http://ubuntuforums.org/archive/index.php/t-219510.html)
case sensitive = true

# [http://softwarecommunity.intel.com/articles/eng/1259.htm](http://softwarecommunity.intel.com/articles/eng/1259.htm)
strict allocate = yes

socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=131072 SO_SNDBUF=131072

and then normal stuff:

   security = user
  passdb backend = smbpasswd:/etc/samba/smbpasswd

   obey pam restrictions = no

   guest account = nobody
   invalid users = root

   preserve case = yes



the switch might not support jumbo. i will have to look. it didn't appear to have any real effect either way. the socket options in smb.conf i think was the biggest performance improvement if i recall.

i'm testing by copying a 360 meg file (or 500) and using "time"

time cp file /mnt/sambashare

it's not the best, but it consistently gives me an idea.

i use xbox media center, which only supports samba right now. perhaps if i get the linux version going, i can use NFS. but right now, i do still need samba around.

i know cifs isn't the best, but i figured with machines not doing that much more and disks that say according to hdparm they can do at least 60 megs/sec, i'd be able to get more...

---

### Post by glennodotcom on 2008-02-10
For whats its worth I have been living under a rock and hadn't realised the world had moved on from smbfs to cifs!

Under Gutsy (AMD64) on a new Dell with a Intel 82566DC n/w card (e1000 driver) with smbfs i couldn't achieve anything better than 6.5MB per sec when copying ISO's from my Dlink DNS-323 NAS through a 1Gb switch.

Under Windows I could achieve 22MB per sec so something on the gutsy side of things was the issue.

Researching the e1000 driver I figured a few people had issues, so I installed the latest module code from Intel - no difference.

Came out from under my rock and changed my mounts from smbfs to cifs and speed picked up to 21MB per sec.

I think at these speeds im starting to hit limitations outside of the network side of things.

---

