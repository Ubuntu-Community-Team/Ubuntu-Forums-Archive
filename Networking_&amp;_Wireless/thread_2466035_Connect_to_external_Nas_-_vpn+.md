---
title: "Connect to external Nas - vpn+?"
date: 2021-08-18
forum: Networking &amp; Wireless
---

### Post by kaktux on 2021-08-18
Hi there,

My brother and I want to use a Qnap Nas together.
We already were able to get a VPN Connection working (openvpn) - and are able to access/open the files from everywhere using dolphin via smb://. But this way we can not edit files on the nas - they have to be saved locally and then moved. Opening+saving on the nas doesn't work. So for now i created a folder with files i work on and sync them to the nas via freefilesync

So my question is: is there a way to a add the nas drive in a way that you can use it like a local drive? 
Also preferred: as the vpn connection needs to be up to access the nas - a way to add the nas drive whenever the vpn connection is active?

any hint would be great.

---

### Post by TheFu on 2021-08-18
This is more a question about QNAP than Linux or Ubuntu.
If the QNAP supports NFSv4 with Kerberos, then you can and it will be both secure and as fast as possible.  CIFS is not a good protocol for WAN storage access.
The other option is also dependent on the QNAP.  Does it support ssh?  If it does, then you can mount the remote storage over sshfs. This will be much slower and some lessor used file system capabilities won't work, but it is possible.

If you want to share just for stuff like streaming media and steaming audio files, then there are better solutions. All of them start by using a full VPN. Which VPN should be used depends on a number of factors and how much security you seek.  openvpn requires very careful configuration to ensure leaks and poor settings don't undermine everything.  wireguard is much simpler and probably similarly secure to openvpn. It also connects very fast, so the connection can be on-demand.  If you want stronger security, use IPSec.

I wouldn't run any VPN on a router or NAS device.  That's just asking to be hacked, IMHO.  I run my VPNs on dedicated VPN servers (actually virtual machines), so there is only 1 thing on that system - used for 1 purpose.  This makes dependency problems that break upgrades nearly non-existent.

WAN performance will matter greatly in any of these solutions, usually the upload bandwidth will be the main problem on both sides for non-commercial connections. If both sides have Gbps fibre connections, that truly is a game changer. I'm jealous.  However, there are speed-of-light problems if the locations aren't in within 50 miles of each other (as the network sees it).  Plus, when the internet isn't available, if the NAS isn't on your LAN, there will be issues.  

If you have Ubuntu, it really could make sense to have a local 10TB HDD and treat it like a "NAS", then perform daily replication to the remote NAS more as a backup.  Use rsync for this - assuming QNAP supports rsync over ssh or you mount it locally and rsync like it is a local disk. rsync treats network-based synchronization very different from local sync, so you'll probably be better off using the network sync that a local mount of the remote QNAP storage.

---

